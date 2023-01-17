node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

//     stage('Build image') {
  
//        app = docker.build("ornate-unity-358911/test-0/vinay")
//     }
    
        stage('Build image') {
  
       app = docker.build("vinaay/test")
    }

    stage('Test image') {
  

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        
        docker.withRegistry('https://registry.hub.docker.com', 'Docker') {
            app.push("${env.BUILD_NUMBER}")
        }
    }
    
    stage('Trigger ManifestUpdate') {
                echo "triggering updatemanifestjob"
                build job: 'updatemanifest', parameters: [string(name: 'DOCKERTAG', value: env.BUILD_NUMBER)]
        }
    
//      script {
//                 docker.withRegistry('https://gcr.io', 'gcr:gcp_demo') {
//                     app.push("${env.BUILD_NUMBER}")
//                 }
//             }



}
