node('master')
{
    stage('ContinuousDownload')
    {
        git 'https://github.com/satish016/dev.git'
    }
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: '33045fd6-02cf-4e2b-8ec3-8e41bd030373', path: '', url: 'http://172.31.40.52:8080')], contextPath: 'qaenv', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/satish016/testing.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/testing/testing.jar'
    }
    stage('ContinuesDelivery')
    {
        deploy adapters: [tomcat9(credentialsId: '42e3b7b0-416d-41fd-bb46-231ae525da1f', path: '', url: 'http://172.31.45.212:8080')], contextPath: 'prodenv', war: '**/*.war'
    }
}