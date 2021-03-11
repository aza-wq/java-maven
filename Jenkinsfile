pipeline {
    agent any
    tools {
        maven 'maven-3.6'
    }
    stages {
        stage ("build jar") {
            steps {
                script {
                    echo "building the application ..."
                    sh 'mvn package'
                }

            }

        }

        stage ("build image"){
            steps {
                script {
                    echo "building docker image"
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-repo', passwordVariable: 'PASS', usernameVariable: 'USER')])

                        sh 'docker build -t aza/demo-app:jma-2.0 .'
                        sh "docker login -u $USER --password-stdin"
                        sh 'docker push aza/demo-app:jma-2.0 .'
                }

            }

        }

        stage ("deploy"){
                    steps {
                        script {
                            echo "deploying application .."
                        }

                    }

                }
    }


















 }
