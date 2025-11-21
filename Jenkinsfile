pipeline {
      agent any
      stages{
        // Création image
        stage('Création de  image docker') {
            steps {
                sh 'docker build -t cv_tbui .'
            }
            post {
                success {
                    echo "====++++Docker image created with success++++===="
                }
                failure {
                    echo "====++++Docker image failed++++===="
                }
            }
        }

          // Création container
        stage('Lancer un container de cette image') {
            steps {
                sh 'docker run -d -p 8099:80 --name cv_tbui_cont cv_tbui'
            }
            post {
                success {
                    echo "====++++Container started with success++++===="
                }
                failure {
                    echo "====++++Failed to start Container++++===="
                }
            }
        }
      }
}