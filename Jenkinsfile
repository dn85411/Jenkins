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
				   

		bat '''Desktop\\vs-bash-console.bat
			make prod'''

		bat "\"${tool 'MSBuild-Default'}\\MSBuild.exe\" D:\\CIS_Source\\Source\\Master.sln "
		bat '"C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Professional\\Common7\\IDE\\devenv.com" "D:\\CIS_Source\\Source\\Master.sln" /Build "Release" /Project "D:\\CIS_Source\\Source\\Install\\AIM PACIS SCU Install\\AIM PACIS SCU Install.vdproj"'
		bat '"C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Professional\\Common7\\IDE\\devenv.com" "D:\\CIS_Source\\Source\\Master.sln" /Build "Release" /Project "D:\\CIS_Source\\Source\\Install\\AIM PACIS Server Install\\AIM PACIS Server Install.vdproj"'
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
