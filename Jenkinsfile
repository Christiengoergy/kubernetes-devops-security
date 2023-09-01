pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
<<<<<<< HEAD
              archive 'target/*.jar' 
=======
              archive 'target/*.jar' //so that they can be downloaded\
>>>>>>> c5618dc5aef3416beb997e357997357a7594e0c0
            }
        }   
    }
}
