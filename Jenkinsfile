@Library('library')_

pipeline{
    agent any
    stages{
        stage('ContDownload_master'){
            steps{
                script{
                    devopps.newGit("maven")
                }
            }
        }
        
        stage('ContBuild_master'){
            steps{
                script{
                    devopps.newBuild()
                }
            }
        }
     }
  }
