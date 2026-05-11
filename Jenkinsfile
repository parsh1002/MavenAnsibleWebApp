pipeline{
agent any
tools{
maven  'Maven'
}
stages{
stage('Checkout'){
steps{
git branch: 'main',url:'https://github.com/parsh1002/MavenAnsibleWebApp.git'
}
}
stage('Build'){
steps{
sh 'mvn clean package'
}
}
stage('Archive'){
steps{
archiveArtifacts artifacts : 'target/*.war', fingerprint:true
}
}
stage('Deploy'){
steps{
sh 'mvn clean package'
sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
}
}
}
post{
success{
ehco 'succ'
}
failure{
echo 'failure'
}
}
}
 
