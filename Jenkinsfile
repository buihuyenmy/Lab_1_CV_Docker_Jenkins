pipeline {
      agent any
      stages{

        // Supprimer container
        stage('Etape 1: Arreter containers') {
            steps {
                sh 'docker stop cv_tbui_cont'
                sh 'docker rm cv_tbui_cont'
            }
            post {
                success {
                    echo "====++++Containers stop with success++++===="
                }
                failure {
                    echo "====++++Docker ailed to stop containers++++===="
                }
            }
        }
        // Création image
        stage('Etape 2: Création de  image docker') {
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
        stage('Etape 3: Lancer un container de cette image') {
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