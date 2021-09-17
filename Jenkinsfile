pipeline {
    agent 'any'
    stages {
        stage('git_clone') {
            steps {
            echo 'cloning the code from repo'
            git branch: 'main', credentialsId: 'aecb30cd-09b3-4f86-bcaf-cbcc2cafecb8', url: 'https://github.com/himabindu-sekhar/devops-prasad.git'
            }
        }
        stage('maven_compile') {
        steps {
            echo 'now maven operations are starting'
            sh '''
            cd $WORKSPACE
            ls -ll
            pwd
            mvn clean compile
            '''
        }
    }
    stage('maven_test') {
        steps {
            echo 'now maven operations are starting'
            sh '''
            cd $WORKSPACE
            ls -ll
            pwd
            mvn test
            '''
        }
    }
    stage('code_quality') {
        steps {
            echo 'now maven operations are starting'
            sh '''
            cd $WORKSPACE
            ls -ll
            pwd
            mvn sonar:sonar
            '''
        }
    }
     stage('package') {
        steps {
            echo 'now maven operations are starting'
            sh '''
            cd $WORKSPACE
            ls -ll
            pwd
            mvn package
            '''
        }
    }
    stage('jfrog_deployment') {
        steps {
            sh '''
            echo 'deploying files to jfrog'
             curl -u admin:Admin@123 -T /c/Users/HIMABINDHU/.jenkins/workspace/Jenkinsfile-Pipelinejob/target/com.google-google.jar "http://localhost:8081/artifactory/devops-files/."
        '''
        }
    }
    }
}
