def tmsp = "${BUILD_ID}" 
def buildnum = "${BUILD_NUMBER}"
def path = "D:\\CIS_JENKINS\\${JOB_NAME}\\${BUILD_NUMBER}"

pipeline {
	
   agent {
    node {
      	label 'master'
	    
	    customWorkspace "${path}"
        }
     }
    stages {
        stage('Build') {

            steps {
		    
                echo 'Building..' 
		echo "${WORKSPACE}"		
		echo "${tmsp}"
		echo "${buildnum}"
		checkout scm
				   
		powershell '''cd "D:\\cis\\Source\\CORE\\LIVE"
				rebar compile'''
		 

		bat "\"${tool 'MSBuild-Default'}\\MSBuild.exe\" D:\\cis\\Source\\Master.sln "
		bat '"C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Professional\\Common7\\IDE\\devenv.com" "D:\\cis\\Source\\Master.sln" /Build "Release|x64"'
		
	    }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
  post {
  	always {    
	  dir("${path}@tmp") {
      	  deleteDir()
    }
  }
}

}
