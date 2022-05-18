pipeline {
  agent {
    node {
      label 'windows_slave_01'
    }

  }
  stages {
    stage('Build') {
      steps {
        bat 'mvn -B -DskipTests clean package'
      }
    }

    stage('Test') {
      post {
        always {
          junit 'target/surefire-reports/*.xml'
        }

      }
      steps {
        bat 'mvn test'
      }
    }

    stage('Deployment Stage') {
      steps {
        bat 'java -jar C:/jenkins_slave_01/workspace/pipeline_job/target/jenkins-example-1.0-SNAPSHOT.jar'
      }
    }
  }
}
