pipeline {
    agent { label 'Neeha' }
 tools{
  maven 'm3'
 }
    stages {
        stage('build') {
         tools{
             maven 'm3'
               }
         steps {
                echo 'Clean Build'
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
                sh 'mvn test'
            }
        }
        
        stage('Sonar') {
            steps {
                echo 'Sonar Scanner'
          withSonarQubeEnv('sonar') {
                sh 'mvn sonar:sonar -Dsonar.login=admin -Dsonar.password=admin -Dsonar.host.http://34.69.20.65:9000'
          }
          }
        }
        stage('Package') {
            steps {
                echo 'Packaging'
                sh 'mvn package'
            }
        
    
        }
        stage('deploy') {
            steps {
                echo 'deploy'
                sh 'mvn deploy'
            }
        }
    }
    
}
