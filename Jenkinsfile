pipeline{
    agent any
    stages{
        stage("Input")
        {
            steps{
                env.YourTag = input  message: 'What are we deploying today?',ok : 'Deploy',id :'tag_id',
                                        parameters:[chodescription: 'Select a tag for this build', name: 'TAG')]
            }
        }
    }
}