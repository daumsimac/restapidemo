node {
  stage("Clone the project") {
    git branch: 'main', url: 'https://github.com/daumsimac/restapidemo.git'
  }

  stage("Compilation") {
    sh "chmod +x ./gradlew"
    sh "./gradlew clean build -x test"
  }

  stage("Tests and Deployment") {
    stage("Running unit tests") {
      sh "chmod +x ./gradlew"
      sh "./gradlew test"
    }
    stage("Deployment") {
      sh "chmod +x ./gradlew"
      sh 'nohup ./gradlew bootRun -Dserver.port=8080 &'
      sh 'echo #!ASdf2580 | docker login -u daumsimac@gmail.com --password-stdin'
      sh 'docker build -t daumsimac/restapidemo:1.0 .'
      sh 'docker push daumsimac/restapidemo:1.0'
    }
  }
}
