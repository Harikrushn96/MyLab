pipeline {
    //Directives
    agent any
    tools {
        maven 'M2_HOME'
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'
            }
        }

        stage  ('Deployment to nexus repo'){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-0.0.8.war', type: 'war']], credentialsId: 'nexus-token', groupId: 'com.vinaysdevopslab', nexusUrl: '192.168.33.22:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'project-1', version: '0.0.8'
            }
        }        
        // Stage3 : Publish the source code to Sonarqube
        // stage ('Sonarqube Analysis'){
        //     steps {
        //         echo ' Source code published to Sonarqube for SCA......'
        //         withSonarQubeEnv('sonarqube'){ // You can override the credential to be used
        //              sh 'mvn sonar:sonar'
        //         }
        //     }
        // }
    }
}
