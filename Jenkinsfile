node {
  stage('Build Docker Image'){
  parallel(
      a: {
        echo "Build Myweb1"
        sh "docker pull sonarqube"
        try {
          sh 'docker rmi gskrscm/sonarqube_image_1'
        }
        catch{
          echo 'Image1 is not there'
        }
        sh "docker run -itd --name sonarqube1 sonarqube"
        sh "docker commit sonarqube1 gskrscm/sonarqube_image_1"
      },
      b: {
        echo "Build Myweb2"
        try {
          sh 'docker rmi gskrscm/sonarqube_image_2'
        }
        catch{
          echo 'Image2 is not there'
        }
        sh "docker pull sonarqube"
        sh "docker run -itd --name sonarqube2 sonarqube"
        sh "docker commit sonarqube2 gskrscm/sonarqube_image_2"
      }
    )
  }
}
