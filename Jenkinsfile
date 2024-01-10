node('built-in')
{
    stage('ContinousDownload')
    {
        git 'https://github.com/ANYA-123/maven.git'
    }
    stage('ContinousBuild')
    {
        sh 'mvn package'
    }
     stage('ContinousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: '4ba9a36c-6b0c-4856-a3a2-79207e94dce8', path: '', url: 'http://172.31.0.204:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinousTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    stage('ContinousDelivery')
    {
        deploy adapters: [tomcat9(credentialsId: '4ba9a36c-6b0c-4856-a3a2-79207e94dce8', path: '', url: 'http://172.31.7.254:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
