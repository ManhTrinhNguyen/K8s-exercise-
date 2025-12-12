pipeline { // Defines the entire pipeline
    agent any 
    tools {
      gradle 'gradle'
    }
    stages { 
      stage('Increment Version') {
        steps {
          script {
            echo "Increment patch version"
            sh "gradle patchVersionUpdate"
            def major = readProperties file : 'version.properties.major'
            echo "${major}"
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
