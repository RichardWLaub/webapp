node {
    stage('Build') {
        git "https://github.com/$GITHUB_ID/webapp.git"
        sh "docker image build -t $DOCKERHUB_ID/jenkins-build ."
    }
    stage('Test') {
        sh "docker container run --rm $DOCKERHUB_ID/jenkins-build /usr/bin/python /opt/webapp/tests.py"
    }
    stage('Push') {
      withCredentials([usernamePassword(credentialsId: 'docker', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
        sh 'docker login -u $USERNAME -p $PASSWORD'
      }
      sh "docker push $DOCKERHUB_ID/jenkins-build"
    }
}
