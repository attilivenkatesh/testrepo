pipeline {
    agent any
    tools {
        gradle 'gradle5'
    }

    stages {
        stage('Test1') {
            steps {
                echo 'Test1..'

                // get code from our Git repository
                git url:'https://github.com/attilivenkatesh/testrepo.git',  branch: 'develop', credentialsId: '7b4950fd-1bd8-489f-b35a-98ddb0808fa8'
                
                 // run Gradle to execute compile and unit testing
                sh "gradle release -Prelease.useAutomaticVersion=true -Prelease.releaseVersion=1100.0.7 -Prelease.newVersion=1100.0.8-SNAPSHOT"

            }
        }
        stage('Test2') {
            steps {
                echo 'Test2..'

                git tag -d "v1100.0.7"

                // get code from our Git repository
                git url:'https://github.com/attilivenkatesh/testrepo1.git',  branch: 'develop', credentialsId: '7b4950fd-1bd8-489f-b35a-98ddb0808fa8'
                
                 // run Gradle to execute compile and unit testing
                sh "gradle release -Prelease.useAutomaticVersion=true -Prelease.releaseVersion=1100.0.7 -Prelease.newVersion=1100.0.8-SNAPSHOT"
                
            }
        }
        stage('Test3') {
            steps {
                echo 'Test3....'
            }
        }
    }
}