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
            def major = versionProps['major']
            def minor = versionProps['minor']
            def patch = versionProps['patch']
            env.APP_VERSION = "${major}.${minor}.${patch}"
            echo "${APP_VERSION}"
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
