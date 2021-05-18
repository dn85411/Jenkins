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
				   
		bat '"C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Professional\\VC\\Auxiliary\\Build\\vcvarsall.bat" x64'
		bat '''cd D:\\CIS_Source\\Source\\CORE\\LIVE
		"C:\\Program Files\\Git\\bin\\bash.exe" -c "make prod"'''

		bat '"C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Professional\\Common7\\IDE\\devenv.com" "D:\\CIS_Source\\Source\\Master.sln" /Rebuild "Release|x64"
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
