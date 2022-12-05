declerative pipeline:

pipeline
{
    agent any
        stages
        {
            stage('contDownload')
            {
                steps{
                    git 'https://github.com/intelliqittrainings/maven.git'
                }
            }
            stage('contBuild')
            {
                steps{
                    sh 'mvn package'
                }
            }
            stage('contDeploy')
            {
                steps{
                    deploy adapters: [tomcat9(credentialsId: '56a88edb-c2cd-463a-9a99-f06ebe5228b6', path: '', url: 'http://172.31.87.243:8080')], contextPath: 'testapp', war: '**/*.war'
                }
            }
            stage('contTesting')
            {
                steps{
                    git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                    sh 'java -jar /var/lib/jenkins/workspace/DeclerativePipeline1/testing.jar'
                }
            }
            stage('contDelivery')
            {
                steps{
                    deploy adapters: [tomcat9(credentialsId: '56a88edb-c2cd-463a-9a99-f06ebe5228b6', path: '', url: 'http://172.31.80.100:8080')], contextPath: 'myprodapp', war: '**/*.war'
                }
            }
        }
}
