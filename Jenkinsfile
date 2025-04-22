pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/AlwinChong02/practical_8_github_action.git'
            }
        }
        stage('Build') {
            steps {
                bat 'start gradlew build'
                //bat 'gradle build'
                //powershell 'gradlew build'
            }
        }
        stage('Test') {
            steps {
                bat 'start gradlew test'
                //bat 'gradle test'
                //powershell 'gradle test'
            }
        }
        stage('Deploy') {
            steps {
                def jarFile = bat(script: 'dir /b build\\libs\\*.jar', returnStdout: true).trim()
                powershell "java -jar build/libs/${jarFile}.jar"
            }
        }
    }

post { 
    always 
    { 
        echo 'Cleaning up workspace' 
        deleteDir() // Clean up the workspace after the build 
    } 
    success { 
        echo 'Build succeeded!!!' // You could add notification steps here 
    } 
    failure { 
        echo 'Build failed!' // You could add notification steps here 
    } 
    } 
}
