pipeline {
      agent any
      stages{
        // Création image
        stage('Création de  image docker') {
            steps {
                sh 'docker build -t cv_mezghich .'
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

          // Création image
        stage('Lancer un container de cette image') {
            steps {
                sh 'docker run -d -p 8081:80 cv_mezghich_cont cv_mezghich'
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