node {
def mvnHome = tool 'maven-3.8.2'
def image
   //1//  stage ('checkout') {
       git 'https://github.com/nithish407/myfirstapp.git'
        }
   
 //2//   stage ('Build') {
       // def mvnHome = tool name: 'maven', type: 'maven'    
         mvnHome = tool 'maven-3.8.2' 
         def mvnCMD = "${mvnHome}/bin/mvn "
         sh "${mvnCMD} clean package"           
        }
       
       
   //3// stage ('Docker Build') {
         
            docker.build('springboot')
        }
 //4// stage ('Docker push')
    docker.withRegistry('https://<accountno>.dkr.ecr.ap-south-1.amazonaws.com', 'ecr:ap-south-1:test-ecr') {
    docker.image('springboot').push('latest')
        }


