pipeline {

  agent any
  environment {
    //adding a comment for the commit test
    DEPLOY_CREDS = credentials('deploy-anypoint-user')
    MULE_VERSION = '4.3.0'
    BG = "NJC"
    WORKER = "Micro"
    ENVIRONMENT = 'Sandbox'
  }
  stages {
    stage('Build Application') {
      steps {
            sh 'mvn -B -U -e -V clean -DskipTests package'
          }
    }
    stage('Deploy Application to cloudhub') {
      steps {
            sh 'mvn -U -V -e -B -DskipTests deploy -DmuleDeploy -Dmule.version="$MULE_VERSION" -Danypoint.username="$DEPLOY_CREDS_USR" -Danypoint.password="$DEPLOY_CREDS_PSW" -Dcloudhub.app="$APP_NAME" -Dcloudhub.environment="$ENVIRONMENT" -Dcloudhub.bg="$B" -Dcloudhub.worker="$WORKER"'
      }
    }
   
  }
}
