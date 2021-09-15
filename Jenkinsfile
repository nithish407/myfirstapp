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
     stage ('uploading to ecr') {
          
               echo "uploading to docker ECR" 
               sh 'docker tag springboot:latest 910130889522.dkr.ecr.us-east-1.amazonaws.com/springboot:latest'
               sh 'docker push 910130889522.dkr.ecr.us-east-1.amazonaws.com/springboot:latest'
              /* sh 'aws ecs update-service --cluster Fargate-Network-Stack-ECSCluster-IdxQDQgqYdau --service springboot--task-definition springboot:4 --desired-count 1 --force-new-deployment'*/
        
     }


}
