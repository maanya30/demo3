pipeline {
 agent any
 tools {
 maven 'Maven'
 jdk 'JDK21'
 }
 stages {
 stage('Checkout') {
 steps {
 git branch:'master',
 url:'https://github.com/SKYFALLrumbles/3.git'
 }
 }
 stage('Build') {
 steps {
 sh 'mvn clean compile'
 }
 }
 stage('Test') {
 steps {
 sh 'mvn test'
 }
 }
 stage('Package') {
 steps {
 sh 'mvn package''
   sh 'mvn package'
 }
 }
 stage('Run Application') {
 steps {
 sh 'mvn exec:java -Dexec.mainClass="com.example.app.App"'
 }
 }
 }
 post {
 success {
 emailext (
 subject: "SUCCESS: ${JOB_NAME} #${BUILD_NUMBER}",
 body: "Build succeeded!\nCheck: ${BUILD_URL}",
 to: "bskoushik06@gmail.com"
 )
 }
 failure {
 emailext (
 subject: "FAILED: ${JOB_NAME} #${BUILD_NUMBER}",
 body: "Build failed!\nCheck: ${BUILD_URL}",
 to: "bskoushik06@gmail.com"
 )
 }
 }
}
