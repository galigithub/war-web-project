node {
   tools {
      maven 'M3'
   }
   
   stage('Checkout') {
      checkout scm
   }
   
   stage('Build') {
      sh 'mvn -B -DskipTests clean package'
   }
   
   stage('Package') {
      xldCreatePackage artifactsPath: 'build/libs', manifestPath: 'deployit-manifest.xml', darPath: '$JOB_NAME-$BUILD_NUMBER.0.dar'
   }
   /*
   stage('Deploy') {
      xldDeploy serverCredentials: 'tomcat', environmentId: 'Environments/Dev', packageId: 'Applications/<project_name>/$BUILD_NUMBER.0'
   }  
   */
}
