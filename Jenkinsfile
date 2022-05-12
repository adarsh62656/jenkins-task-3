def tagid = null
pipeline{
    agent any
    stages{
        stage("Input")
        {
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