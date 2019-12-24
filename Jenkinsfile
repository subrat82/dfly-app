node{
  def Namespace = "default"
  def ImageName = "subratit/projects-16th-dec"
  def ImageTag = "latest"
  def Creds	= "076eed1a-ddda-4fcc-b8bd-5fbf6fa738fd"
  //def Creds ="c3VicmF0aXQ6U2FzbWl0YTEyMyo"

  stage('Checkout'){
      
    git branch: 'master',
    credentialsId: 'cd86d294-d343-4a1b-8e19-388f2ac2f93b',
    url: 'https://github.com/subrat82/dfly-app.git'
  }
  stage('Docker Build, Push'){
      sh "/usr/local/bin/docker --version"
      sh "echo docker login localhost:8080"
      sh "/usr/local/bin/docker build -t ${ImageName}:${ImageTag} ."
      sh "echo build successfully"
      sh "/usr/local/bin/docker push ${ImageName}"
      sh "echo push successfully"
      withDockerRegistry([credentialsId: "${Creds}", url: 'https://index.docker.io/v1/']) 
      //withDockerRegistry([credentialsId: "076eed1a-ddda-4fcc-b8bd-5fbf6fa738fd", url: 'https://index.docker.io/v1/']) {
      //withDockerRegistry([url: 'https://index.docker.io/v1/']) {

        

    }
}
