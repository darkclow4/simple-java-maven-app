node {
    docker.image('maven:3.8.1-adoptopenjdk-11').inside('-v /root/.m2:/root/.m2') {
        stage('Build') {
            sh 'mvn -B -DskipTests clean package'
        }
        stage('Test') {
            sh 'mvn test'
        }
        stage('Manual Approval') {
            input message: 'Lanjutkan ke tahap Deploy? (Click "Proceed" untuk melanjutkan)'
        }
        stage('Deploy') {
            sh './jenkins/scripts/deliver.sh'
            sleep(60)
        }
    }
}