pipeline {
agent any // Use any available agent
environment {
LANG = 'en_US.UTF-8'
LC_ALL = 'en_US.UTF-8'
}
tools {
maven 'Maven' // Ensure this matches the name configured in Jenkins
}
stages {
stage('Checkout') {
steps {
git branch: 'master', url 'https://github.com/adithyaS360/labint.git
}
}
stage('Build') {
steps {
sh 'mvn clean package'
}
}
stage('Archive') {
steps {
archiveArtifacts artifacts: 'target/Labinternal.war', fingerprint:true
}
}
stage('Deploy') {
steps {
sh 'mvn clean package'
sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
}
}
}
}
