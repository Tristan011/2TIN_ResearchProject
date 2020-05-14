pipeline {
   agent any

   stages {
      stage('Clean-up') {
         steps {
            deleteDir() //Iets anders gopzoeken om te ebruiken??
            echo 'Clean-up directory'
         }
      }
      stage('fetch-code') {
        steps {
            git 'https://github.com/roelpxl/2TIN_ResearchProject.git'
            echo 'Code van git gehaald'
        }
      }
      stage('Build'){
          steps{
              sh 'composer install' //In centos7 moet een link aangemaakt worden naar publiek bin directory
              echo 'Build'
              
          }
      }
      stage('test'){
          steps{
              sh './vendor/bin/phpunit tests build/phpunit.xml'
              echo 'unittest uitgevoerd' //TODO testen in een file zetten
          }
      }
      stage('Artifact'){
          steps{
              //dir()
              archiveArtifacts artifacts: '**', onlyIfSuccessful: true //alles archiveren van de repo --> locatie: /var/lib/jenkins/jobs/...
          }
      }
      stage('Mysql database update'){
          steps{
              sh 'mysql -u root -pMysqllaatmebinnen1! employees </var/lib/jenkins/workspace/SNB2_pipeline/employees.sql'
              //move file to github
              //sql connection: 'localhost root Mysqllaatmebinnen1! employees'
              //sql: 'SELECT * FROM employees;'
              echo 'Mysql updaten door .sql file in repo' //TODO pmugin voor Mysql in jenkins
          }
      }
      stage('Deploy to Apache'){
          steps{
              sh 'sudo cp -R /var/lib/jenkins/workspace/SNB2_pipeline/* /var/www/html/'
              echo'Deployment of repo to live'
          }
      }
      }
      }
