node ("slave") {
    stage ('checkout') {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/RahulKumar1119/sample-java-app.git']]])
}

    stage ('Build') {
        sh 'mvn -f ./pom.xml clean package'   
}

    stage ('Tomcat Deploy') {
        deploy adapters: [tomcat9(credentialsId: 'ac9f20ff-8dcb-4bcd-ac6a-5430dd55e3c1', path: '', url: 'http://3.7.65.40:8080/')], contextPath: 'sample-java-app', onFailure: false, war: '**/*.war'
}
}
