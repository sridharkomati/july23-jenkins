pipeline {
    tools {
        jdk 'JDK-8'
        maven 'mvn-gol' 
    }
    agent { label 'JDK-8'}
    triggers { pollSCM('* * * * *') }
    stages { 
        stage('Build Maven Project'){
                steps{
                    git branch: 'master',
                        url: 'https://github.com/wakaleo/game-of-life.git'
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
        //                 url: 'https://github.com/wakaleo/game-of-life.git'
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
}

