
pipeline {
    agent any
    stages {
        stage ('pipeline1') {
            steps {
                git branch: 'main', url: 'https://github.com/SidduChintu/Ansible.git'
            }
        }
        
        stage ('execute ansible.yml'){
            steps {
                ansiblePlaybook credentialsId: 'Ansible2', disableHostKeyChecking: true, installation: 'ansible', inventory: 'host.inv', playbook: 'ansible.yml'
            }
        }
        
        stage ('email') {
            steps {
                emailext body: '''$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:

                 Check console output at $BUILD_URL to view the results.''', subject: 'This application is deployed', to: 'nsrm47@gmail.com'
            }
        }
    }
}
