pipeline {
    agent any
    stages{
        stage('Get Apis'){
            steps{
                git url: 'https://github.com/vit-dperez/test_dir.git'
            }
        }
        stage('Populate parameters'){
            steps{
                script{
                    def apiList = []
                    def files = findFiles()

                    files.each{ f ->
                        if(f.directory){
                            apiList.add(f.name)
                            //writeFile file: 'api-list', text: "${f.name}"
                        }
                    }
                    // echo "${apiList}"
                    writeFile file: 'api-list', text: "${apiList}"
                }
            }
        }
        stage('Archive the file'){
            steps{
                archiveArtifacts artifacts: 'api-list', followSymlinks: false
            }
        }
    }
}