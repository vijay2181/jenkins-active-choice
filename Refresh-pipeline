properties([
    parameters([
        string(name: 'DEPLOYMENT', defaultValue: '', description: 'Name of deployment'),
        string(name: 'ENVIRONMENT', defaultValue: '', description: 'Name of environment')
    ])
])


node {
    
    stage('clean') {
            sh '''
                > /var/lib/jenkins/workspace/DEPLOYMENTS/Refresh.txt
                > /var/lib/jenkins/workspace/DEPLOYMENTS/services.txt
                echo "${DEPLOYMENT}"
                echo "${ENVIRONMENT}"
              '''
        }
            
    stage('Service list') {
                sh 'python3 /var/lib/jenkins/workspace/DEPLOYMENTS/service_list.py > /var/lib/jenkins/workspace/DEPLOYMENTS/Refresh.txt'
        }
        
    stage('Select Services') {
        script {
            def optionsFile = new File('/var/lib/jenkins/workspace/DEPLOYMENTS/Refresh.txt')
            def options = optionsFile.readLines().findAll{ it.trim() }
            def selectedEnvironments = input message: 'Proceed with build?',
                parameters: [
                    [
                        $class: 'ChoiceParameter',
                        choiceType: 'PT_CHECKBOX',
                        description: 'Select environments',
                        filterLength: 1,
                        filterable: false,
                        name: 'Environment',
                        script: [
                            $class: 'GroovyScript',
                            script: [
                                sandbox: true,
                                script: '''
                                  def optionsFile = new File('/var/lib/jenkins/workspace/DEPLOYMENTS/Refresh.txt')
                                  def options = optionsFile.readLines().findAll{ it.trim() }

                                  return options
                                '''
                            ]
                        ]
                    ]
            ]
            echo "Selected environments: ${selectedEnvironments}"
            env.selectedEnvironments = selectedEnvironments
        }
    }
    stage('shell') {
    script {
        def services = env.selectedEnvironments
        echo "Selected services: ${services}"
        def profile = env.ENVIRONMENT
        echo "Profile: ${profile}"
        sh """
        echo 'hii vijay'
        echo '$services'
        echo '${profile}'

        for service in \$(echo $services | tr ',' ' '); do
           final_service=\$(echo \$service | cut -d ',' -f1 | cut -d ':' -f1)
           echo \$final_service  >> /var/lib/jenkins/workspace/DEPLOYMENTS/services.txt
        done
        """
    }
 }
}
