node {   
   stage('Checkout') {
      git url: 'https://github.com/galigithub/war-web-project'
   }
   
   stage('Build'){
      def maven_version = 'maven3'
      withEnv(["PATH+MAVEN=${tool maven_version}/bin"]) {
         sh "mvn -B -DskipTests clean package"
      }
   }
   
   /*stage('Build') {
      sh 'mvn -B -DskipTests clean package'
   }*/
   
   stage('Package') {
      xldCreatePackage artifactsPath: 'target/*.war', manifestPath: 'deployit-manifest.xml', darPath: '$JOB_NAME-$BUILD_NUMBER.0.dar'
   }
   /*
   stage('Deploy') {
      xldDeploy serverCredentials: 'tomcat', environmentId: 'Environments/Dev', packageId: 'Applications/<project_name>/$BUILD_NUMBER.0'
   }  
   */
   
   /*
   stage('Package') {  
    xldCreatePackage artifactsPath: 'build/libs', manifestPath: 'deployit-manifest.xml', darPath: '$JOB_NAME-$BUILD_NUMBER.0.dar'  
  }  
  stage('Publish') {  
    xldPublishPackage serverCredentials: '<user_name>', darPath: '$JOB_NAME-$BUILD_NUMBER.0.dar'
  }  
  stage('Deploy') {  
    xldDeploy serverCredentials: '<user_name>', environmentId: 'Environments/Dev', packageId: 'Applications/<project_name>/$BUILD_NUMBER.0'
  } 
   */
   
   
   
   
}
