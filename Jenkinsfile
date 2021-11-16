pipeline {
  agent any 
  tools {
    maven "M3"
    }
  stages {
    stage ('Initialize') {
      steps {
        sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
            ''' 
      }
    }
    
   
  
   stage('Build') {
        def mvn_version = 'M3'
        withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] ) {
        sh '''for f in i7j-*; do
                (cd $f && mvn clean package -Dmaven.test.skip=true -Dadditionalparam=-Xdoclint:none  | tee ../jel-mvn-$f.log) &
              done
              wait'''
        }
   }
  
    }
     
   }
    
 

