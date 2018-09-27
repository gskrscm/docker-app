node {
  stage('Build Docker Image'){
  parallel(
      a: {
        echo "Build Myweb1"
        sh "docker build -t 'gskrscm/myweb1:1.0.0' ."
      },
      b: {
        echo "Build Myweb2"
        sh "docker build -t 'gskrscm/myweb2:1.0.0' Dockerfile2"
      }
    )
  }
}
