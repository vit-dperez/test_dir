pipeline {
    agent any
    stages{
        stage('Get Apis'){
            steps{
                //git changelog: false, credentialsId: 'github', poll: false, url: 'https://github.com/vit-dperez/test_dir.git'
                git url: 'https://github.com/vit-dperez/test_dir.git'
            }
        }
    }
}