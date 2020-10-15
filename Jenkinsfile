peline {
    agent any
        stages {
	         stage('checkout') {
		             steps {
			                   checkout changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'githubcred', url: 'https://github.com/rxa80330/Angular-HelloWorld.git']]]
					               }

						               }
							               stage('build') {
								                   steps{
										                 echo 'build'
												               sh '''npm install
													                           npm run build'''
																               }
																	               }
																		               stage('docker-build') {
																			                   steps{
																					                 sh 'docker build -t angular-hw:latest .'
																							              
																								                  } 
																										          }
																											          stage('docker-publish') {
																												              steps{
																													                        
																																                withCredentials([usernameColonPassword(credentialsId: 'dockerhubcreds', variable: 'creds')]) {
																																		                 sh 'docker push ravalianthati/angular-hw:latest'
																																				                 }
																																						             }    
																																							             }
																																								                   
																																										       } 
																																										       }    
																pipeline {
    agent any
    stages {
         stage('checkout') {
            steps {
              checkout changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'githubcred', url: 'https://github.com/rxa80330/Angular-HelloWorld.git']]]
            }

        }
        stage('build') {
            steps{
              echo 'build'
              sh '''npm install
                    npm run build'''
            }
        }
        stage('docker-build') {
            steps{
              sh 'docker build -t angular-hw:latest .'
             
            } 
        }
        stage('docker-publish') {
            steps{
                  
                withCredentials([usernameColonPassword(credentialsId: 'dockerhubcreds', variable: 'creds')]) {
                 sh 'docker push ravalianthati/angular-hw:latest'
                }
            }    
        }
              
    } 
}    
  
