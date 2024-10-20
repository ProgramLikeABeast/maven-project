pipeline {
    agent any
    tools{
        maven 'maven-3.8.4'
    }
    
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo '开始存档....'
                    archiveArtifacts artifacts: '**/target/*.war'
                    sh "sudo /usr/bin/docker build . -t tomcatwebapp:${env.BUILD_ID}"
                }
            }
        }
    }
}
