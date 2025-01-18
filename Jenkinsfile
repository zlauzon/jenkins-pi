pipeline {
    agent any
    options {
        buildDiscarder(logRotator(daysToKeepStr: '10', numToKeepStr: '10'))
        timeout(time: 12, units: 'HOURS')
        timestamps()
    }
    stages {
        stage('Requirements') {
            steps {
                // enable the script to be executed directly from shell
                sh('chmod +x ./algorith.sh')
            }
        }
        stage('Build') {
            steps {
                //creates a file named report.txt
                sh('./algorithm.sh')

                // archives the report
                archiveArtifacts allowEmptyArchive: true, artifacts: '*.txt', fingerprint: true, followSymlinks: false, onlyIfSuccessful: true
            }
        }
    }
}