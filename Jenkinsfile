pipeline {
        agent any

        parameters {
                choice(name: 'ENVIRONMENT', choices: ['QA','UAT'], description: 'Pick Environment value')
        }
        stages {
            stage('Checkout') {
                steps {
                        checkout scm
                      }}
                stage('Build') {
                   steps {
                          sh '/home/hima/dev-software/apache-maven-3.9.6/bin/mvn install'
                         }}
                stage('Deployment'){
                    steps {
                        script {
                         if ( env.ENVIRONMENT == 'QA' ){
                sh 'cp target/prod2.war /home/hima/dev-software/apache-tomcat-9.0.86/webapps'
                echo "deployment has been done on QA!"
                         }
                        else if ( env.ENVIRONMENT == 'UAT' ){
                sh 'cp target/prod2.war /home/hima/dev-software/apache-tomcat-9.0.86/webapps'
                echo "deployment has been done on UAT!"
                        }
                      

                        }}}
}}

