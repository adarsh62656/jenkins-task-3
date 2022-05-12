def tagid = null
pipeline{
    agent none
    stages{
        stage("Input")
        {
            agent none
            steps{
                script{
                    tagid = input(
                        message : 'Enter the Tag ID',
                        ok : 'Submit',
                        parameters: [string(defaultValue:'32' , name:'TAG_ID' , trim=true)]
                    )
                }
            }
        }
    }
}