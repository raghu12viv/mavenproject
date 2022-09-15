node('built-in') 
{
    stage('ContinuousDownload')
    {
       git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContineousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: 'a95d53fa-869f-4cde-b58b-18fb323358e9', path: '', url: 'http://172.31.28.153:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContineousTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/sciptedpipeline/testing.jar'
    }
    stage('ContineousDelivery')
    {
        deploy adapters: [tomcat9(credentialsId: 'a95d53fa-869f-4cde-b58b-18fb323358e9', path: '', url: 'http://172.31.23.122:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
