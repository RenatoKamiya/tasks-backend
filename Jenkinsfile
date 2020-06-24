pipeline {
    agent any
    stages {
        stage ('Build Backend') {
        steps {
            bat 'mvn clean package -DskipTests=True'
        }

      }
      stage ('Unit Tests') {
        steps {
            bat 'mvn test'
            }
        }
        stage ('Sonar Analysis'){
            environment {
                scannerHome = tool 'SONAR_SCANNER'
            }
            steps {
                withSonarQubeEnv( 'SONAR_LOCAL'){
                    bat "${scannerHome}/bin/sonar-scanner -e -Dsonar.projectKey=DeployBack -Dsonar.host.url=http://35.198.21.135:9000 -Dsonar.login=48562ebc5e8295d08d15eeb019025c514e5aa6b5 -Dsonar.java.binaries=target -Dsonar.coverage.exclusions=**/.mvn/**,**/src/test/**,**/model/**,**Application.java "
                }
            }           
        }
    }
}
