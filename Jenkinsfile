pileline{
    agent{
        label 'MAVEN-JDK8'
    }
         environment{
                jdk:'JDK_8_UBUNTU'
            }
    stages{
        stage('vcm'){
       
            steps{
                git url : 'https://github.com/DeveopsSolutions/game-of-life.git',
                    branch :'declarative'
            }
            stage('package'){
                steps{
                   sh 'maven package'
                }
            }

        }
        stage('post build')
           steps{
              archiveArtifacts artifacts: '**/target/gameoflife.war',
              onlyIfSuccessful:true
              junit testResults:'**/surefire-reports/TEST-.**xml'
           }
    }
}