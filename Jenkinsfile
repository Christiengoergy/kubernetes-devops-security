pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' 
            }
        }
      stage('unit test') {
           steps {
              sh "mvn test"   
            }
           post {
            always {
              junit 'target/surefire-reports/*.xml'
              jacoco execPattern: 'target/jacoco.exec'
            }
           } 
        } 
      stage('docker image build and push'){
           steps {
              withDockerRegistry([credentialsId: "docker-hub",url:""]){
                 sh 'printenv' 
                 sh 'docker build -t christiengoergy/numeric-app:""$GIT_COMMIT"" .'
                 sh 'docker push christiengoergy/numeric-app:""$GIT_COMMIT""'
              } 
           }
      }     
  } 
}
