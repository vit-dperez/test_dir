properties([
    parameters([
        [$class: 'ChoiceParameter',
            choiceType: 'PT_SINGLE_SELECT',
            description: 'Select a choice',
            filterLength: 1,
            filterable: true,
            name: 'Api List',
            randomName: 'choice-parameter-7601235200970',
            script: [$class: 'GroovyScript',
                fallbackScript: [classpath: [], sandbox: false, script: 'return ["ERROR"]'],
                script: [classpath: [], sandbox: false, 
                    script: """
                        def PREV_BUILD = ${BUILD_NUMBER}.toInteger() - 1\n
                        def fileContents = readFile("/var/lib/jenkins/jobs/sandbox/jobs/master job/branches/feature-acti.auurjo.plementation/builds/$PREV_BUILD/archive/api-list")\nreturn fileContents
                    """
                ]]]
    ])
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