pipeline{
    tools{
        jdk 'ourjava'
        maven 'ourmaven'
    }
	agent any
      stages{
           stage('Checkout'){
              steps{
		 echo 'cloning..'
                 git 'https://github.com/olujlab/DevOpsCodeDemo.git'
              }
          }
          stage('Compile'){
              steps{
                  echo 'compiling..'
                  sh 'mvn compile'
	      }
          }
          stage('CodeReview'){
              steps{
		    
		  echo 'codeReview'
                  sh 'mvn pmd:pmd'
              }
          }
           stage('UnitTest'){
              steps{
	         echo 'It is now time for Unit Testing'
                  sh 'mvn test'
              }
               post {
               success {
                   junit 'target/surefire-reports/*.xml'
               }
           }	
          }
          stage('Package'){
              steps{
                  sh 'mvn package'
              }
          }
      }
}
