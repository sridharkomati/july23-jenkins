pipeline {
    tools {
        jdk 'JDK-8'
        mvn 'mvn' 
    }
    agent { label 'JDK-8'}
    triggers { pollSCM('* * * * *') }
   stage('Build Maven Project'){
        steps{
            rtMavenDeployer (
                id: "maven-ID",
                serverId: "JFROG",
                releaseRepo: 'qtdevops-libs-release-local',
                snapshotRepo: 'qtdevops-libs-snapshot-local',
                )
            rtMavenRun (
                tool: 'mvn',
                pom: 'pom.xml',
                goals: 'clean install',
                deployerId: "maven-ID",
                )
            rtPublishBuildInfo (
                serverId: "JFROG"
            )    
        }
    }    
    stage('reporting') {
            steps {
                junit testResults: '**/target/surefire-reports/TEST-*.xml'
            }
        }     
// stages { 
//     stage('vcs') {
//         steps {
//             git branch: 'master',
//                 url: 'https://github.com/sridharkomati/july23-jenkins.git'
//         }
//     }    
//     stage('build') {
//         steps {
//             sh 'ls'
//             sh 'java -version' 
//             sh 'mvn --version'
//             sh 'mvn package'
//         }
//     }  
     
}
