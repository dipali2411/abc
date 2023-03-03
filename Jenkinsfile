pipeline {
    agent any
    parameters {
     string description: 'cron', name: 'cron'
     extendedChoice description: 'choice', multiSelectDelimiter: ',', name: 'choice', 
     propertyFile: '/var/lib/jenkins/workspace/test/name.txt', propertyKey: 'env', quoteValue: false, 
     saveJSONParameterToFile: false, type: 'PT_SINGLE_SELECT', visibleItemCount: 5
    }
  
   stages {
        stage('print') {
            steps {
                echo "${params.cron}"
                echo "${params.choice}"
            }
        }

        stage('build a job') {
            steps {
                 build job: 'dsl plugin', parameters: [string(name: 'name', value: String.valueOf(choice))]
            }
        }
        stage('build a job2') {
            steps {
                 build 'cron-test'
            }
        }
        stage('build a job3') {
            steps {
                 build job: 'test-cron-option', parameters: [string(name: 'cron', value: '')]
            }
        }
   }
}

