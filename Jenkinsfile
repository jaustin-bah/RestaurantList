node {
    docker.image("gradle:latest").inside() {
        stage('Checkout') {
            git 'https://github.com/jaustin-bah/RestaurantList.git'
        }
        stage('Build') {
            sh 'chmod +x ./gradlew'
            sh './gradlew clean build'
        }
        stage('Unit Tests') {
            sh './gradlew test --tests RestaurantListApplicationTests'
        }        
        stage('Code Quality') {
            sh './gradlew sonarqube -Dsonar.projectKey=RestaurantList -Dsonar.host.url=http://52.226.64.55:9000 -Dsonar.login=23e7bf7a66f785d6c9180c5391050bdbaaf60c48 -Dsonar.projectName=RestaurantList'
        }
    }
}