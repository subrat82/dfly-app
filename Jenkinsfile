node{
  def Namespace = "default"
  def ImageName = "subratit/projects-16th-nov"
  def ImageTag = "latest02"
  def Creds	= "076eed1a-ddda-4fcc-b8bd-5fbf6fa738fd"


  //try{
  stage('Checkout'){
      
    git branch: 'master',
    credentialsId: 'cd86d294-d343-4a1b-8e19-388f2ac2f93b',
    url: 'https://github.com/subrat82/dfly-app.git'
      
      
      //git 'https://github.com/sasmita016/dfly-app.git'
      sh "git rev-parse --short HEAD > .git/commit-id"
      //imageTag= readFile('.git/commit-id').trim()



  }
  
  stage('Maven Build'){ 
      sh '/Applications/apache-maven-3.6.3/bin/mvn clean install -f "/Users/subrat/.jenkins/workspace/pipeline_dfly-app/dfly/pom.xml"'
    }

  stage('Docker Build, Push'){
      sh "/usr/local/bin/docker --version"
      sh "echo docker login localhost:8080"
      withDockerRegistry([credentialsId: "${Creds}", url: 'https://index.docker.io/v1/']) {
      //withDockerRegistry([credentialsId: "${Creds}, url: 'https://hub.docker.com/'"]) {
      sh "echo hello"
      sh "pwd"
      sh "/usr/local/bin/docker build -t ${ImageName}:${ImageTag} ."
      sh "echo hello1"
      sh "/usr/local/bin/docker push ${ImageName}"
      sh "docker hello2"
          }

    }
    stage('Deploy on K8s'){
        sh "ansible all -m ping"
        sh "echo hello"
        //sh "ansible-playbook /var/lib/jenkins/ansible/sasmita-deploy/deploy1.yml  --user=root --extra-vars ImageName=${ImageName} --extra-vars imageTag=${imageTag} "
    }
  //} 
  //catch (err) {
  //    currentBuild.result = 'FAILURE'
  //  }
//}
}
