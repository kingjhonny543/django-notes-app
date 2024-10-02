@Library("shared") _
pipeline {
    agent { label "ansible" }

    stages {
        stage("Call Shared Library") {
            steps {
                script {
                    hello() // Ensure the hello() function is defined in the shared library
                }
            }
        }

        stage("Clone Repository") {
            steps {
                script {
                    // Ensure the clone function is defined
                    git branch: 'main', url: 'https://github.com/kingjhonny543/django-notes-app.git'
                    echo "Cloning done"
                }
            }
        }

        stage("Build Docker Image") {
            steps {
                script {
                    // Ensure the docker_build function is defined
                    docker_build("notes-app", "latest", "ranchi420")
                }
            }
        }

        stage("Push to Docker Hub") {
            steps {
                script {
                    // Call the corrected docker_push function
                    docker_push("notes-app", "latest", "ranchi420")
                }
            }
        }

        stage("Deploy") {
            steps {
                echo "Deploying the code"
                sh "docker-compose up -d" // Make sure docker-compose is installed and accessible
            }
        }
    }
}
