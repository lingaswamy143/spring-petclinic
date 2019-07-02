node {
    stage('SCM') {
        git 'https://github.com/lingaswamy143/spring-petclinic.git'
    }
    
    stage('Build & Package') {
        withSonarQubeEnv('sonar') {
            sh 'mvn clean package sonar:sonar'
        }
    }
    
}
    