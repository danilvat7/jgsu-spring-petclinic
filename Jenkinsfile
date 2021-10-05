pipeline {
    agent any
      triggers {
        pollSCM('* * * * *')
    }
    stages {
        // stage('Checkout') {
        //     steps {
        //          git branch: 'main', url: 'https://github.com/danilvat7/jgsu-spring-petclinic.git'
        //     }
        // }
        stage('Build') {
            steps {
                sh './mvnw clean package'
                // sh 'true'
            }
            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
                // changed {
                //     emailext attachLog: true,
                //     body: 'Please go to ${BUILD_URL} and verify the build', 
                //     compressLog: true, 
                //     subject: 'Job \'${JOB_NAME}\' (${BUILD_NUMBER}) is waiting for input', 
                //     to: 'danilvat7@gmail.com'
                // }
            }
        }
    }
}
