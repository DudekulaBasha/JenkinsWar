node{

   def tomcatWeb = 'C:\\Program Files\\Apache Software Foundation\\Tomcat 7.0_Tomcat7'
   def tomcatBin = 'C:\\Program Files\\Apache Software Foundation\\Tomcat 7.0_Tomcat7\\bin'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/DudekulaBasha/JenkinsWar.git'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      bat "${mvnHome}/bin/mvn package"
      }
/*   stage ('Stop Tomcat Server') {
               bat ''' @ECHO OFF
               wmic process list brief | find /i "tomcat" > NUL
               IF ERRORLEVEL 1 (
                    echo  Stopped
               ) ELSE (
               echo running
                  "${tomcatBin}\\shutdown.bat"
                  sleep(time:10,unit:"SECONDS") 
               )
'''
   }*/
   
   stage('Deploy to Tomcat'){
     bat " \\Jenkins\\Jenkins.war \"${tomcatWeb}\\webapps\\Jenkins.war\""
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         bat "${tomcatBin}\\startup.bat"
         sleep(time:100,unit:"SECONDS")
   }
}
