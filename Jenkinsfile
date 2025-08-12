node {
  stage('Checkout') {
    checkout scm
  }

  stage('Build') {
    sh 'docker image build -t helmandharmony-hue/demo-api:latest .'
  }

  stage('Push') {
    withCredentials([
        usernamePassword(credentialsId: 'docker-credentials',
                         usernameVariable: 'podfather',
                         passwordVariable: 'dckr_pat_zd22d9suPKVDdFrXlIdO1nK8GYo')]) {
      sh 'docker login -p "${PASSWORD}" -u "${USERNAME}"'
      sh 'docker image push ${USERNAME}/demo-api:latest'
    }
  }

  stage('Deploy') {
    //withCredentials([
    //    file(credentialsId: 'kube-config',
    //         variable: 'KUBECONFIG')]) {
    //  sh 'kubectl apply -f deployment.yaml'
    //}
  }
}
