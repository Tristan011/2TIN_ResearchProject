   node {
	   stage('Node locatie aanpassen'){
		sh 'sudo cp -R var/lib/jenkins/workspace/SNB2_Keuze/* var/lib/jenkins/workspace/SNB2_Keuze@2/'
	   }
	    
      stage('Build'){
              sh 'composer install' 
              echo 'Build'
      }
      stage('test'){
              sh './vendor/bin/phpunit tests build/phpunit.xml'
              echo 'unittest uitgevoerd'
          }
      stage('Artifact'){
              archiveArtifacts artifacts: '**', onlyIfSuccessful: true //alles archiveren van de repo --> locatie: /var/lib/jenkins/jobs/...
      }
      stage('Mysql database update'){
         
              sh 'mysql -u root -pMysqllaatmebinnen1! employees </var/lib/jenkins/workspace/SNB2_pipeline/employees.sql'
              echo 'Mysql updaten door .sql file in repo'
          }
      
      stage('Deploy to Apache'){
         
              sh 'sudo cp -R /var/lib/jenkins/workspace/SNB2_Keuze@2/* /var/www/html/'
              echo'Depoymetn of repo to live'
          
      }
      stage('Post-clean'){
	      
	    //deleteDir() // Dit verwijderd de huidige directory waar deze pipeline in zit
	      echo 'Deleted folder'
   }
 }
