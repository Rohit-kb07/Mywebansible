pipeline {
 agent any
 tools {
 maven 'Maven-3.6.3' // Make sure Maven version is configured in Jenkins global tools
 }
 
 stages {
 stage('Checkout') {
 steps {
 git 'https://github.com/Rohit-kb07/Mywebansible.git'
 }
 }
 stage('Build') {
 steps {
 sh 'mvn clean install' // Build the Maven project
 }
 }
 stage('Archive Artifacts') {
 steps {
 archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
 }
 }
 stage('Deploy') {
 steps {
 ansiblePlaybook playbook: 'playbook.yml', inventory: 'hosts.ini' // Run the Ansible

 }
 }
 }
 post {
 success {
 echo 'Build and deploy completed successfully!'
 }
 failure {
 echo 'Build failed!'
 }
 }
}
