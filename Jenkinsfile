node {
    def app

    stage('Clone repository') {    
      checkout scm
    }

    stage('Build image') {
  
       app = docker.build("ornate-unity-358911/test-0/vinay")
    }

        
     script {
                docker.withRegistry('https://gcr.io', 'gcr:gcp_demo') {
                    app.push("${env.BUILD_NUMBER}")
                }
            }



}
