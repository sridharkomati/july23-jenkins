pipeline {
    tools {
        jdk 'JDK-8'
    }
    agent { label 'JDK-8'}
    triggers { pollSCM('* * * * *') }
stages { 
    stage('vcs') {
        steps {
            git branch: 'master',
                url: 'https://github.com/sridharkomati/july23-jenkins.git'
        }
    }    
    stage('build') {
        steps {
            sh 'ls'
            sh 'java --version' 
            sh 'mvn --version'
            sh 'mvn package'
            

        }
    }    
   }
}
