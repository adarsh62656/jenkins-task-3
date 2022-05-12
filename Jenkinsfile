def tagid = null
pipeline{
    agent any
    stages{
        stage("Input")
        {
            agent none
            steps{
                script{
                    tagid = input(
                        message : 'Enter the Tag ID',
                        ok : 'Submit',
                        parameters : [string(defaultValue: '32' , name: 'TAG_ID')]
                    )
                }
            }
        }
        stage("Deploy")
        {
            agent any
            steps{
                sh "docker pull public.ecr.aws/s5o7d0z2/adarsh-repo:build-${tagid}"
                sh "docker run -p 3000:8080 public.ecr.aws/s5o7d0z2/adarsh-repo:build-${tagid}"
            }
        }
        stage("CLEANUP"){
            sh "docker image prune -a"
        }
    }
}