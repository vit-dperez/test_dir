pipeline {
    agent any
    stages{
        stage('Get Apis'){
            steps{
                git url: 'https://github.com/vit-dperez/test_dir.git'
            }
        }
        stage('Populate parameters'){
            environment {
                API = ''
                apiList = []
            }
            steps{
                script{
                    def apiList = []
                    def files = findFiles()

                    files.each{ f ->
                        if(f.directory){
                            apiList.add(f.name)
                        }
                    }
                    echo "${apiList}"
                }
            }
        }
        stage('Select the APIs'){
            steps{
                script{
                    env.API = input message: 'Select the APIs', ok: 'Select', parameters: [extendedChoice(value: "${apiList}", name: 'APIs',type: 'PT_MULTI_SELECT', multiSelectDelimiter: '\n')]
                    echo "${env.API}"
                }
            }
        }
    }
}