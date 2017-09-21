#!/usr/bin/env groovy
pipeline {

environment
{
BuildNumber="${BUILD_NUMBER}"
HSF_3PP="${env.WORKSPACE}/3pp"
BuildPathOutput="${WORKSPACE}\\..\\builds\\"
MyWorkSpace="${env.WORKSPACE}"
MYHSF3PP="$MyWorkSpace/3pp"
}

	agent any
    tools
  {
    ant "Ant1.9.9"
  }
  



  stages {
  	stage('Read Properties') {

  steps {
	      echo "3pp is ${HSF_3PP}"
  	
  			readProperties(file: 'C:/Prashant/.hudson/PSBuild/SetEnvironment.properties')
  		}
  	}
    stage('print') {
   
	 steps {
		println "JOB_NAME = $JOB_NAME"
        //echo "3pp is ${env.HSF_3PP}"
        echo "${WORKSPACE}"
        echo "${BUILD_NUMBER}"
		echo "${env.BuildNumber}"
		echo "$HSF_3PP"
		//echo "BuildPathOutput is ${BuildPathOutput}"
        echo bat(returnStdout: true, script: 'env')

      }
    }
     stage('Test Env') {
	 environment
	 {
		HSF_PSPS="$WORKSPACE/3pp"
	 }
       steps {
			withEnv(["HSF_MYPP=$WORKSPACE/3pp"])
			{
				bat 'C:/Prashant/.hudson/PSBuild/TestEnv.bat'
			}
       }
	}
  }
}
