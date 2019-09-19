  //Checkout Code from Git
  checkout scm

//Stage 1 : Build the docker image.
  stage('image') {
      sh("snap install docker")
  }

  //Stage 1 : Build the docker image.
  stage('Build image') {
      sh("docker build -t ${imageTag} .")
