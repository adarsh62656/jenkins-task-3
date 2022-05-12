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
        stage("Approval")
        {
            agent none
            def userInput = false
            script {
            def userInput = input(id: 'Proceed1', message: 'Promote build?', parameters: [[$class: 'BooleanParameterDefinition', defaultValue: true, description: '', name: 'Please confirm you agree with this']])
            echo 'userInput: ' + userInput
            if(userInput == true) {
                // do action
            } else {
                // not do action
                echo "Action was aborted."
            }

        }
        }
        stage("CLEANUP"){
            sh "docker image prune -a"
        }
    }
}