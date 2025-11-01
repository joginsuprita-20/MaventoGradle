pipeline {
    agent any  // Use any available agent

    tools {
        // Ensure this matches the name of the Gradle installation in Jenkins
        gradle 'Gradle'  
        jdk 'JDK 17'  // Ensure this matches the JDK configured in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Hemavathipcse/GradleJenkinsPipeline.git'
            }
        }

        // Added this stage to check Gradle version
        stage('Verify Gradle Version') {
            steps {
                echo 'Verifying Gradle version...'
                sh './gradlew --version'  // This will print the Gradle version being used during the build
            }
        }

        // Added this stage to check Java version
        stage('Verify Java Version') {
            steps {
                echo 'Verifying Java version...'
                sh 'java -version'  // This will print the Java version used during the build
            }
        }

        stage('Build') {
            steps {
                echo 'Building the Gradle project...'
                sh './gradlew clean build'  // Run Gradle build instead of Maven
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh './gradlew test'  // Run tests with Gradle
            }
        }

        stage('Run Application') {
            steps {
                echo 'Running the generated jar file...'
                sh 'java -jar build/libs/MyMavenToGradle-1.0-SNAPSHOT.jar'  // Run the Gradle JAR
            }
        }
    }

    post {
        success {
            echo '✅ Build and deployment successful!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
