pipeline{
    agent any
    stages{
        stage("Input")
        {
            steps{
                script{
                    properties([
                        parameters([
                            text(
                                defaultValue: '''
                                this is a multi-line 
                                string parameter example
                                ''', 
                                 name: 'MULTI-LINE-STRING'
                            )
                        ])
                    ])
                
                }
            }
        }
    }
}