node {
    stage('Nuova versione software su SCM') { 
     git 'https://github.com/SimonPocket/Sample-for-nexus.git'
     //git changelog: false, credentialsId: '46181515-4ea5-4099-970a-5732ee274f7a', poll: false, url: 'https://gitlab.tim.it/timdevops/simon-test.git'


    }
   
   stage('Test di codice con SonarQube'){
    
        def x = fileExists 'sonar-project.properties'
        
        assert x == true //blocca la pipeline se non è stato configurato il file di properties
        
        //input ''
        
        def scannerHome = tool 'scanner 2.8';
    
        //println("${scannerHome}")
    
        withSonarQubeEnv {
            
            sh "ls"
            
            //sh "${scannerHome}/bin/sonar-scanner"
        
            //build job: 'Quality-Gate', quietPeriod: 1
        
        }

    } 
 

   
   stage('Creazione artefatto e Push su nexus'){
        def mvnHome= tool 'Maven' 
        sh "${mvnHome}/bin/mvn deploy -s settings.xml"
        sh "ls"
        sh "${mvnHome}/bin/mvn clean"
        //println("Content: " +response.content)
        //  sh returnStdout: true, script: 'ansible -m command -a \"/home/stefano/NODEJS/DevOps/BuildANDRun.sh\" docker-machine'
       
   }
 stage{'Deploy su Openshift'){
     echo 'hello'
     
 }
   //stage('buildandrun con curl') {
//     input ''
  //   sh returnStdout: true, script: 'curl -i 172.16.1.9:800 | grep \'OK\''
      //junit '**/target/surefire-reports/TEST-*.xml'
      //archive 'target/*.jar'
    //} 

    stage('Smoke Test') {
        //input ''
   
        def response = httpRequest 'http://sonarqube.156.54.176.146.xip.io'
        
        //println("Status: " +response.status)
        if( response.status==200 ){
            echo 'Correttamente Funzionante'
            }
        
        else echo 'Errore'
        
    } 
}
