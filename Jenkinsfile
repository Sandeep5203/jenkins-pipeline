node {
   def mvnHome
  stage('Prepare') {
      git url: 'https://github.com/Sandeep5203/jenkins-pipeline.git', branch: 'sandy'
      mvnHome = tool 'maven'
   }
  stage ('Clean') {
      sh "'${mvnHome}/bin/mvn' clean"
  }
  stage ('Validate') {
      sh "'${mvnHome}/bin/mvn' validate"
  }
  stage ('Compile') {
      sh "'${mvnHome}/bin/mvn' compile"
  }
  stage ('Test') {
      sh "'${mvnHome}/bin/mvn' test"
  }
  stage ('Package') {
      sh "'${mvnHome}/bin/mvn' package"
  }
  stage ('Verify') {
      sh "'${mvnHome}/bin/mvn' verify"
  }
  stage ('Install') {
      sh "'${mvnHome}/bin/mvn' install"
  }
  
}
stage('Stage-8 : Deploy an Artifact to Artifactory Manager i.e. Nexus/Jfrog') { 
            steps {
                sh 'mvn deploy'
            }
        }
          stage('Stage-9 : Deployment - Deploy a Artifact devops-2.0.0-SNAPSHOT.war file to Tomcat Server') { 
            steps {
                sh 'curl -u admin:redhat@123 -T target/**.war "http://54.174.26.178:8080/manager/text/deploy?path=/8amDevOps&update=true"'
            }
        } 
          stage('Stage-10 : SmokeTest') { 
            steps {
                sh 'curl --retry-delay 10 --retry 5 "http://54.174.26.178:8080/8amDevOps"'
            }
        }

    }
}
