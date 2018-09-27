node {
  stage('Build Docker Image'){
  parallel(
      a: {
        echo "Build Myweb1"
        sh "docker pull sonarqube"
        try {
          sh 'docker rmi gskrscm/sonarqube_image_1'
          sh ''
        }
        catch(error){
          echo 'Image1 is not there'
        }
        sh "docker run -itd --name -p 9001:9000 sonarqube1 sonarqube"
        sh "docker commit sonarqube1 gskrscm/sonarqube_image_1"
      },
      b: {
        echo "Build Myweb2"
        try {
          sh 'docker rmi gskrscm/sonarqube_image_2'
        }
        catch(error){
          echo 'Image2 is not there'
        }
        sh "docker pull sonarqube"
        sh "docker run -itd --name -p 90002:9000 sonarqube2 sonarqube"
        sh "docker commit sonarqube2 gskrscm/sonarqube_image_2"
      }
    )
  }
}
