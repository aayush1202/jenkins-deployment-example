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
        echo 'deploying...'
      }
    }

    stage('Sonar-Report') {
      steps {
        bat 'mvn clean install sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.analysis.mode=publish org.codehaus.sonar-plugins.pdf-report:maven-pdfreport-plugin:1.3:generate'
      }
    }

  }
}