pipeline {
  agent any
stages {
  stage ('Build') {
    steps {
      sh 'printenv'
    }
  }
stage ('Publish to ECR') {
      steps {
         withEnv(["AWS_ACCESS_KEY_ID=${env.AWS_ACCESS_KEY_ID}", "AWS_SECRET_ACCESS_KEY=${env.AWS_SECRET_ACCESS_KEY}", "AWS_DEFAULT_REGION=${env.AWS_DEFAULT_REGION}"]) {
        sh 'docker login -u AWS -p $(aws ecr-public get-login-password --region us-east-1)'
        sh 'docker build -t ecr-demoimg .'
        sh 'docker tag ecr-demoimg:latest public.ecr.aws/x3k9c4u8/ecr-demoimg:latest'
        sh 'docker push public.ecr.aws/x3k9c4u8/ecr-demoimg:latest'
         }
      }
 }
}
}
