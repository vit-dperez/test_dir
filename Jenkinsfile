pipeline {
    agent any
    stages{
        stage('Get Apis'){
            steps{
                step{
                    git changelog: false, credentialsId: 'github', poll: false, url: 'https://github.com/vit-dperez/test_dir.git'
                }
            }
        }
    }
}