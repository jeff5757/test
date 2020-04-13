pipeline{
    agent(label 'master'){
        stages{
            stage('git repo download'){
                step{
                    script{
                        git credentialsId: 'ab3dc1cd-f4c2-4721-87a4-0c01891fa71d', url: 'https://github.com/jeff5757/gameoflife-1.git'
                    }
                }
            }

 
            stage('maven compilation'){
                step{
                    script{
                        withMaven(jdk: 'jdk8', maven: 'maven'){
                            sh 'mvn clean install'
                        }
                    }
                }
            }

 
            stage('nexus artifacy upload'){
                step{
                    script{
                        nexusArtifactUploader credentialsId: 'nexus', groupId: 'be.cegeka', nexusUrl: '13.233.3.65:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'Releases', version: '0.0.1'
                    }
                }
            }
        }
    }
}

