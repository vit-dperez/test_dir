def paramsListEnd= [
        gitParameter(
            branchFilter: 'origin/(.*)', //filtering this common part of all branch names
            defaultValue: 'master', 
            name: 'BRANCH', 
            type: 'PT_BRANCH'
        )
    ]

properties([
    parameters(
       paramsListEnd)
])

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
                apiList1 = ''
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
                    env.apiList1 = apiList
                }
            }
        }
        stage('Select the APIs'){
            steps{
                script{
                    env.API = input message: 'Select the APIs', ok: 'Select', parameters: [extendedChoice(value: "${apiList1}", name: 'APIs',type: 'PT_MULTI_SELECT', multiSelectDelimiter: '\n')]
                    echo "${env.API}"
                }
            }
        }
    }
}