pipeline{
    agent{
        label 'MAVEN_JDK8'
    }
    stages{
        stage('scm'){
            steps{
                git url : 'https://github.com/DeveopsSolutions/game-of-life.git',
                    branch :'declarative'
            }
        }
        stage('package'){
                 tools {
                        jdk 'JDK_8_UBUNTU'
                         }
                steps{
                   sh 'mvn package'
                }
            }
        stage('post build'){
                steps{
                    archiveArtifacts artifacts: '**/target/gameoflife.war',
                    onlyIfSuccessful:true
                    junit testResults:'**/surefire-reports/TEST-*.xml'
               }
            }
    }
}