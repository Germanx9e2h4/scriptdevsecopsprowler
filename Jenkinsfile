//import org.jenkinsci.plugins.pipeline.modeldefinition.Utils

pipeline{
    
    agent any 
    stages {

        stage('prowler DEV html') {
            steps {
                script{
                    catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                sh 'sudo /var/lib/jenkins/workspace/prowler/prowler -p "TU PERFIL" -M html'
                }
              }
            }
        }


        stage('prowler cp files DEV') {
            steps {
                script{
                   sh 'sudo cp /var/lib/jenkins/workspace/prowler/output/prowler-output-IDCUENTA* /var/lib/jenkins/workspace/prowler/output/IDCUENTA-dev'
                }
            }
        }


        stage('prowler cp S3 DEV') {
            steps {
                script{
                   sh 'sudo aws s3 cp /var/lib/jenkins/workspace/prowler/output/IDCUENTA-dev/ s3://prowlersuperapp/IDCUENTA-dev/ --profile "PERFIL DE TU CUENTA" --recursive'
                }
            }
        }



    }
}
