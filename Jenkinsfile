pipeline {
  agent any

  tools {
    maven "MAVEN3.9"
    jdk "JDK17"
  }

  environment {
    registryCredential = credentials('AWS_CREDENTIAL_ID')
    imageName = "${env.ECR_IMAGE_NAME}"
    vprofileRegistry = "${env.ECR_REGISTRY}"
  }

  stages {
    stage('Fetch code') {
      steps {
        git branch: 'docker', url: 'https://github.com/example/repository.git'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn install -DskipTests'
      }
      post {
        success {
          echo "Archiving artifact"
          archiveArtifacts artifacts: '**/*.war'
        }
      }
    }

    stage('Unit Test') {
      steps {
        sh 'mvn test'
      }
    }

    stage('Checkstyle Analysis') {
      steps {
        sh 'mvn checkstyle:checkstyle'
      }
    }

    stage('SonarQube analysis') {
      environment {
        scannerHome = tool 'SONAR6.2'
      }
      steps {
        withSonarQubeEnv('sonarserver') {
          sh '''${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=vprofile \
          -Dsonar.projectName=vprofile-repo \
          -Dsonar.projectVersion=1.0 \
          -Dsonar.sources=src/ \
          -Dsonar.java.binaries=target/test-classes/com/visualpathit/account/controllerTest/ \
          -Dsonar.junit.reportsPath=target/surefire-reports/ \
          -Dsonar.jacoco.reportsPath=target/jacoco.exec \
          -Dsonar.java.checkstyle.reportPaths=target/checkstyle-result.xml'''
        }
      }
    }

    stage("Quality Gate") {
      steps {
        timeout(time: 1, unit: 'HOURS') {
          waitForQualityGate abortPipeline: true
        }
      }
    }

    stage('Build App Image') {
      steps {
        script {
          dockerImage = docker.build( imageName + ":$BUILD_NUMBER", "./Docker-files/app/multistage/" )
        }
      }
    }

    stage('Upload App Image') {
      steps {
        script {
          docker.withRegistry( vprofileRegistry, registryCredential ) {
            dockerImage.push("$BUILD_NUMBER")
            dockerImage.push('latest')
          }
        }
      }
    }

    stage('Clean Up') {
      steps {
        sh 'docker rmi -f $(docker images -a -q)'
      }
    }
  }

  post {
    always {
      echo 'Slack Notifications.'
      slackSend channel: '#build-notifications',
        message: "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}"
    }
  }
}