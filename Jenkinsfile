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
          stage('I am doing CodeReview o'){
              steps{
		    
		  echo 'I am doing codeReview o'
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
