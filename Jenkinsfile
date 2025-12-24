pipeline {
    agent any
    
    triggers {
        pollSCM('H/2 * * * *')
    }
    
    environment {
        COMPOSE_PROJECT = 'aos'
    }
    
    stages {


        stage('Build JAR') {
            steps {
                sh 'chmod +x ./mvnw || true'
                sh './mvnw clean package -DskipTests'
            }
        }
        

        
        stage('Deploy') {
            steps {

                sh '''
                    docker compose -p ${COMPOSE_PROJECT} stop app || true
                    docker compose -p ${COMPOSE_PROJECT} rm -f app || true
                '''
                
                sh '''
                    docker compose -p ${COMPOSE_PROJECT} up -d --build --force-recreate --no-deps app
                '''

            }
        }
        

    }
    
    post {
        success {
            echo 'Done'
            echo "Swagger UI: http://localhost:8080/swagger-ui/index.html"
        }
        failure {
            echo '❌ Pipeline провалился!'
        }
    }
}

