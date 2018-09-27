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
        sh "docker run -itd --name sonarqube1 -p 9001:9000 -p 9092:9092 sonarqube"
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
        sh "docker run -itd --name sonarqube2 -p 9002:9000 -p 9093:9092 sonarqube"
        sh "docker commit sonarqube2 gskrscm/sonarqube_image_2"
      }
    )
  }
}
