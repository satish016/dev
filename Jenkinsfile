node ('')
{
    stage ('ContinuesDownload')
    {
        git 'https://github.com/satish016/dev.git'
    }
    stage ('ContinuesBuild')
    {
       sh 'mvn package'
    }
    stage ('ContinuesDeploy')
    {
       deploy adapters: [tomcat9(credentialsId: '13d2cabb-8675-40aa-92de-f356b532aa07', path: '', url: 'http://172.31.39.129:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage ('ContinuesTesting')
    {
       git 'https://github.com/satish016/testing.git'
       sh 'java -jar /var/lib/jenkins/workspace/dev/testing.jar'
    }
    stage ('ContinuesDelivery')
    {
        deploy adapters: [tomcat9(credentialsId: '5396b98f-65f7-486f-82e4-20edcc86266a', path: '', url: 'http://172.31.1.183:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}