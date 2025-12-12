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
            def versionProps = readProperties file : 'version.properties'
            echo "${versionProps}"
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
