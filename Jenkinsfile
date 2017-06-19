node {
    stage('Build') {
        git 'https://github.com/RichardWLaub/webapp.git'
        sh "docker image build -t jenkins-build ."
    }
    stage('Test') {
        sh "docker container run --rm jenkins-build /usr/bin/python /opt/webapp/tests.py"
    }
}
