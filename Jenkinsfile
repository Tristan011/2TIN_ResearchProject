pipeline {
    agent any
        stages{
            stage('Fetch code'){
                steps{
                git 'https://github.com/Tristan011/jenkins-example.git'
                }
            }
            stage('Build'){
                steps{
                    withMaven{ //hiervoor moet plugin 'pipeline-maven' geinstalleer worden
                       sh 'mvn clean compile'
                    }
                }
            }
            stage('Test'){
                steps{
                    withMaven{ //hiervoor moet plugin 'pipeline-maven' geinstalleer worden
                        sh 'mvn test'
                    }
                }
            }
            stage('Artifact'){
                steps{
                    archiveArtifacts artifacts: '**', onlyIfSuccessful: true
                }
            }
            stage('Deployment stage'){
                steps{
                    //withMaven{ //hiervoor moet plugin 'pipeline-maven' geinstalleer worden
                        //sh 'mvn deploy'
                        //sh 'javac javatestrun.java'
                        //sh 'cd target/classes/com/techprimers/testing/'
                        //sh 'cd src/main/java/com/techprimers/testing/'
                        //sh 'javac -sourcepath src/main/java/com/techprimers/testing/ FizzBuzz.java'
                        //sh 'java -sourcepath src/main/java/com/techprimers/testing/ FizzBuzz'
                        sh 'cd target/classes/com/techprimers/testing/ java FizzBuzz'
                    //}
                }
            }
            stage('Post clean-up'){
                steps{
                    echo 'Delete folders'
                }
            }
            
        }
    
}
