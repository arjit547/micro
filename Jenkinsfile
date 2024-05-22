pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                script {
                    // Compile the Java source code
                    sh 'javac -d out App.java'
                }
            }
        }

        stage('Package') {
            steps {
                script {
                    // Create the JAR file
                    sh 'jar cfm SimpleJavaProject.jar manifest.mf -C out .'
                }
            }
        }

        stage('Archive') {
            steps {
                script {
                    // Archive the JAR file as a build artifact
                    archiveArtifacts artifacts: 'SimpleJavaProject.jar', fingerprint: true
                }
            }
        }

        stage('Copy to Specific Location') {
            steps {
                script {
                    // Copy the project directory to a specific location
                    sh 'cp -r /var/jenkins_home/workspace/mc1 /app/data/mc1'
                }
            }
        }
    }
}
