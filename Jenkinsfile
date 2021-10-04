def continueBuild = true
pipeline {
    agent any

    stages {
        stage ('compile maven') {
            
            steps{
            script{
                try {
                     sh 'mvn compile'
                     } catch(Exception e) {
                      echo '[FAILURE] Failed to build'
                      continueBuild = false
                      currentBuild.result = 'ABORTED'
                      error('Stopping early…')
              }
                }            
        }
        }
        
        stage ('testmaven') {
            steps {
             script{
            if (!continueBuild) {
                 currentBuild.result = 'ABORTED'
                  error('Stopping early…')
                                }
                 
                 try {
                      sh 'mvn tes'
                     } finally {
                      echo '[FAILURE] Failed to build' 
                      continueBuild = false
                      currentBuild.result = 'ABORTED'
                      error('Stopping early…')
                      return testmaven
                 
              }
                
                    }  
   
                
            }
        }
      
        stage ('build maven') {
            steps {
                 script{
            if (!continueBuild) {
                 currentBuild.result = 'ABORTED'
                  error('Stopping early…')
                                }
               try {
               
                    sh 'mvn package'
                    } finally {
                      echo '[FAILURE] Failed to build' 
                      currentBuild.result = 'ABORTED'
                      error('Stopping early…')
              }
                
            }
        }
    }
}
}
