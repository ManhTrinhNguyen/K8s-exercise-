pipeline { // Defines the entire pipeline
    agent any 
    tools {
      gradle 'gradle'
    }
    environment {
      ECR_REPO = '660753258283.dkr.ecr.us-west-1.amazonaws.com'
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
        stage('Build App') { 
            steps { 
                script {
                  echo "Build App"
                  sh "gradle clean build"
                }
            }
        }
        stage('Container App') {
            steps {
                script {
                  echo "Container Gradle App then Push it into AWS ECR"
                  withCredentials([usernamePassword(credentialsId: 'ecr_credential', usernameVariable: 'USER', passwordVariable: 'PWD')]){
                    sh """
                      docker build -t ${ECR_REPO}/java-gradle:${APP_VERSION} .
                      echo "${PWD} | docker login --username "${USER}" --password-stdin "${ECR_REPO}"
                    """
                  }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }
}
