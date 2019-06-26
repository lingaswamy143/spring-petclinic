node {
    stage('SCM') {
        git 'https://github.com/lingaswamy143/spring-petclinic.git'
    }
    
    stage('Build & Package') {
        withSonarQubeEnv('sonar') {
            sh 'mvn clean package sonar:sonar'
        }
    }
    
    stage("Quality Gate") {
        timeout(time: 1, unit: 'HOURS') {
              def qg = waitForQualityGate()
              if (qg.status != 'OK') {
                  error "Pipeline aborted due to quality gate failure: ${qg.status}"
              }
          }
    }
}
    