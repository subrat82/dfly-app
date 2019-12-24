node{
  def Namespace = "default"
  def ImageName = "subratit/projects-16th-nov"
  def ImageTag = "latest02"
  def Creds	= "076eed1a-ddda-4fcc-b8bd-5fbf6fa738fd"

  stage('Checkout'){
      
    git branch: 'master',
    credentialsId: 'cd86d294-d343-4a1b-8e19-388f2ac2f93b',
    url: 'https://github.com/subrat82/dfly-app.git'
  }

    stage('Deploy on K8s'){
        sh "id"
        sh "/usr/local/bin/ansible localhost -m ping"
        sh "echo ansible ran successfully"
        //sh "/usr/local/bin/ansible-playbook -v /Users/subrat/.jenkins/workspace/pipeline_dfly-app/deploy1.yml  --user=root --extra-vars ImageName=${ImageName} --extra-vars imageTag=${ImageTag} --extra-vars ansible_sudo_pass=Sasmita123* "
        //sh "/usr/local/bin/ansible-playbook -vvv /Users/subrat/.jenkins/workspace/pipeline_dfly-app/deploy1.yml --extra-vars ImageName=${ImageName} --extra-vars imageTag=${ImageTag}"
        sh "/usr/local/bin/ansible-playbook -vv /Users/subrat/.jenkins/workspace/pipeline_dfly-app/deploy1.yml --extra-vars ImageName=${ImageName} --extra-vars imageTag=${ImageTag} --extra-vars ansible_sudo_pass=Sasmita123*"

    }
}
