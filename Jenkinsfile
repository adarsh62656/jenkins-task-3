def tagid = null
def userInput = false
pipeline{
    agent any
    stages{
        stage("Input"){
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
        stage("Deploy"){
            agent any
            steps{
                sh "docker pull public.ecr.aws/s5o7d0z2/adarsh-repo:build-${tagid}"
                sh "docker run -p 3000:8080 public.ecr.aws/s5o7d0z2/adarsh-repo:build-${tagid}"
            }
        }
        stage("Approval"){
            agent none
            steps{
                script {
                    userInput = input(id: 'Proceed1', message: 'Promote build?', parameters: [[$class: 'BooleanParameterDefinition', defaultValue: true, description: '', name: 'Please confirm you agree with this']])
                    echo 'userInput: ' + userInput
                    if(userInput == true) {
                    } else {
                        echo "Action was aborted."
                    }
                }
            }
        }
        stage("CLEANUP"){
            steps{
            sh "docker image prune -a"
            }
        }
    }
}
