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
   
   stage('Nexus push'){
      /*nexusPublisher nexusInstanceId: 'mynexus3', nexusRepositoryId: 'maven-snapshots', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'target/SampleWebApp-1.0.0.war']], mavenCoordinate: [artifactId: 'sample', groupId: 'com.sh.test', packaging: 'war', version: '1.0']]]*/
      nexusArtifactUploader artifacts: [[artifactId: 'myapp', classifier: '', file: 'target/SampleWebApp-1.0.0.war', type: 'war']], credentialsId: 'admin123456', groupId: 'com.sh', nexusUrl: '173.255.116.180:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'maven-snapshots', version: '1.0'
   }
   
   /*stage('Build') {
      sh 'mvn -B -DskipTests clean package'
   }*/
   /*
   stage('Package') {
      //xldCreatePackage artifactsPath: 'target/*.war', manifestPath: 'deployit-manifest.xml', darPath: '$JOB_NAME-$BUILD_NUMBER.0.dar'
      xldCreatePackage artifactsPath: 'target', darPath: 'myapp.dar', manifestPath: 'deployit-manifest.xml'
   }
   
   stage('Deploy') {
      //xldDeploy serverCredentials: 'tomcat', environmentId: 'Environments/Dev', packageId: 'Applications/<project_name>/$BUILD_NUMBER.0'
      xldDeploy environmentId: 'Environments/Dev/sampleEnv', packageId: 'Applications/DevApp/warapp/sampleWar', serverCredentials: 'Admin-credentials'
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
