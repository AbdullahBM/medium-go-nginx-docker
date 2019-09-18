node{

  def namespace = 'ingress-default'
  def imageTag = "abdullahbm/gohello"
  
  //Checkout Code from Git
  checkout scm
  
//Stage 0 : Install the docker image.
  stage('Install Docker') {
      sh("sudo apt-get update")
      sh("sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common")
    sh("curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -")
    sh("sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"")
   sh("sudo apt-get update")
   sh("sudo apt-get install docker-ce docker-ce-cli containerd.io")
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

