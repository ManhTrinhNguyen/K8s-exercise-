pipeline { // Defines the entire pipeline
    agent any 
    tools {
      gradle 'gradle'
    }
    stages { 
      stage('Increment Version') {
        steps {
          script {
            echo "Increment version"
          }
        }
      }
        stage('Build') { 
            steps { 
                echo 'Starting build process...'
            }
        }
        stage('Test') {
            steps {
                echo 'Running test cases...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }
}
