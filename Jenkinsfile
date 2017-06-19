node {
    stage('Build') {
        git 'https://github.com/RichardWLaub/webapp.git'
        sh "docker build -t jenkins-test-build ."
    }
}
