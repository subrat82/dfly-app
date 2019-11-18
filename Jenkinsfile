node{
  def Namespace = "default"
  def ImageName = "subratit/projects-16th-nov"
  def imageTag = "latest"
  def Creds	= "a8ff2ad3-db22-4690-b050-7b8dba184426"
  try{
  stage('Checkout'){
      
    git branch: 'master',
    credentialsId: '8bea435f-adf8-498a-b563-fcae25406345',
    url: 'https://github.com/sasmita016/dfly-app.git'
      
      
      //git 'https://github.com/sasmita016/dfly-app.git'
      sh "git rev-parse --short HEAD > .git/commit-id"
      //imageTag= readFile('.git/commit-id').trim()



  }
  
  stage('Maven Build'){ 
      sh 'mvn clean install -f "/var/lib/jenkins/workspace/test-pipeline-4/dfly/pom.xml"'
    }

  stage('Docker Build, Push'){
    withDockerRegistry([credentialsId: "${Creds}", url: 'https://index.docker.io/v1/']) {
      sh "docker build -t ${ImageName}:${imageTag} ."
      sh "docker push ${ImageName}"
        }

    }
    stage('Deploy on K8s'){
        sh "ansible all -m ping"
     sh "ansible-playbook /var/lib/jenkins/ansible/sasmita-deploy/deploy1.yml  --user=root --extra-vars ImageName=${ImageName} --extra-vars imageTag=${imageTag} "
    }
     } catch (err) {
      currentBuild.result = 'FAILURE'
    }
}
