pipeline {
    agent any
//     tools{
//         maven 'Maven_Home'
//     }
    stages {
        stage ('Build') {
            steps {
              echo 'successfully'
//                  sh 'mvn clean package'    
              bat 'dotnet publish  C:Usersmanjula.rAppDataLocalJenkins.jenkinsworkspaceweb123  --configuration Release'
            }
            post{
                 success{
                     echo "Archiving the Artifacts"
                     archiveArtifacts artifacts: '**/target/*.war'
                    
                 }
            }
        }
   
        stage ('Deploy') {
            steps {
                deploy adapters: [tomcat8(credentialsId: '21ea2bf6-8c27-4873-b754-a7a6b9159a0f', path: '', url: 'http://localhost:9090/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
