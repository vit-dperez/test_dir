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
                        }
                    }
                    //echo "${apiList}"
                    input message: 'Select the APIs', ok: 'Select', parameters: [choice(choices: apiList, name: 'APIs')]
                }
            }
        }
        stage('Select the APIs'){
            steps{
                script{
                    //input message: 'Select the APIs', ok: 'Select', parameters: [choice(choices: [apiList], name: 'APIs')]
                    echo "This is the end of the pipeline?"
                }
            }
        }
    }
}