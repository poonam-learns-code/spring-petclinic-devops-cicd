pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Cloning Java Application from GitHub...'
                git branch: 'main', url: 'https://github.com/spring-projects/spring-petclinic.git'
            }
        }

        stage('SonarQube Code Analysis') {
            steps {
                echo 'Running SonarQube Scanner...'
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn clean compile org.sonarsource.scanner.maven:sonar-maven-plugin:sonar'
                }
            }
        }

        stage('Package Application') {
            steps {
                echo 'Packaging application into JAR...'
                sh 'mvn package -DskipTests'
            }
        }

        stage('Docker Build & Package') {
            steps {
                echo 'Creating Dockerfile and Building Docker Container Image...'
                sh '''
                    cat << 'EOF' > Dockerfile
                    FROM eclipse-temurin:17-jre-alpine
                    WORKDIR /app
                    COPY target/*.jar app.jar
                    EXPOSE 8080
                    ENTRYPOINT ["java", "-jar", "app.jar"]
EOF
                    docker build -t java-app:latest .
                '''
            }
        }

        stage('Deploy Application') {
            steps {
                echo 'Deploying Docker Container on EC2...'
                sh '''
                    docker stop my-java-app || true
                    docker rm my-java-app || true
                    docker run -d --name my-java-app -p 8081:8080 java-app:latest
                '''
            }
        }
    }
}
