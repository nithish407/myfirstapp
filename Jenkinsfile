node {
def mvnHome = tool 'maven-3.8.2'
def image
     stage ('checkout') {
       git 'https://github.com/nithish407/myfirstapp.git'
        }
   
   stage ('Build') {  
         mvnHome = tool 'maven-3.8.2' 
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
        }
       
       
   stage ('Docker Build') {
         
            docker.build('springboot')
        }
 //4// stage ('Docker push')
    docker.withRegistry('https://<accountno>.dkr.ecr.ap-south-1.amazonaws.com', 'ecr:ap-south-1:test-ecr') {
    docker.image('springboot').push('latest')
        }


}
