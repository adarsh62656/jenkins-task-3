pipeline{
    agent any
    stages{
        stage("Input")
        {
            steps{
                script{
                env.YourTag = input  message: 'What are we deploying today?',ok : 'Deploy',id :'tag_id',
                                        parameters:[description: 'Select a tag for this build', name: 'TAG']
                }
            }
        }
    }
}