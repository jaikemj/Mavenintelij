def skipRemainingStages = false
pipeline {
    agent any

    stages {
        stage ('compile maven') {
            steps {
               
                    sh 'mvn comple'
                 script {
                    skipRemainingStages = true

                    println "skipRemainingStages = ${skipRemainingStages}"
                }
            }
        }
       
        stage ('test maven') {
            when {
                expression {
                    !skipRemainingStages
                }
            }
            steps {
               
                    sh 'mvn test'
                
            }
        }
      
        stage ('build maven') {
            when {
                expression {
                    !skipRemainingStages
                }
            }
            steps {
               
                    sh 'mvn package'
                
            }
        }
    }
}
