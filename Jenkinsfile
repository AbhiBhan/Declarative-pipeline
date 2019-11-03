def workspace;
node {
    stage('checkout') {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/mitreid-connect/simple-web-app.git']]])
        workspace =pwd()
    }
    stage('compile') {
        sh "/home/abhishek/apache-maven-3.6.2/bin/mvn install"
    }
        stage('deploy') {
            deploy adapters: [tomcat8(credentialsId: 'a67ce3c7-3723-4344-8bd7-db4a298e3b2c', path: '', url: 'http://localhost:8080')], contextPath: 'simple-web-app', war: '**/*.war'
        }
}
    
