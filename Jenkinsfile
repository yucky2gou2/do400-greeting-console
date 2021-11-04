pipeline{
    agent{
        label "nodejs"
    }
    stages{
        stage("Install dependencies"){
            steps{
                sh "npm ci"
            }
        }

        stage("Check Style"){
            steps{
                sh "npm run lint"
            }
        }

        stage("Test"){
            steps{
                sh "npm test"
            }
        }
        stage('Release') {
            steps {
                sh '''
                oc project lhfqsx-greetings
                oc start-build greeting-console --follow --wait
                '''
            }
        }

        // Add the Release stage here
    }
}
