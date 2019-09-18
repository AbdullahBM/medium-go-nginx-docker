node{

  def namespace = 'ingress-default'
  def imageTag = "abdullahbm/gohello"
  
  //Checkout Code from Git
  checkout scm

//Stage 1 : Build the docker image.
  stage('image') {
      sh("snap install docker")
  }

  //Stage 1 : Build the docker image.
  stage('Build image') {
      sh("docker build -t ${imageTag} .")
  }
  
  //Stage 2 : Push the image to docker registry
  stage('Push image to registry') {
      sh("docker push ${imageTag}")
  }
  
  //Stage 3 : Deploy Application
  stage('Deploy Application') {
           sh("kubectl set image deployment/ingress-default ingress-default=abdullahbm/gohello:latest --namespace=${namespace}")
}
}

