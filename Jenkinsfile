pipeline {
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
            sh 'export PATH="/usr/lib/jvm/java-8-openjdk-amd64/bin:$PATH"'
            sh 'ls'
            sh 'java -version' 
            sh 'mvn --version'
            sh 'mvn package'
            

        }
    }    
   }
}
