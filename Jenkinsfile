def label = "kubepod"
def serviceaccount = "jenkins-admin"
podTemplate(label: label, serviceAccount: serviceaccount,imagePullSecrets: ['amrutha'],
            containers: [
                containerTemplate(name: 'python', image: 'python:3-alpine', ttyEnabled: true, command: 'cat'),
                containerTemplate(name: 'helm', image: 'lachlanevenson/k8s-helm', command: 'cat', ttyEnabled: true, priviledged: true),
                containerTemplate(name: 'maven', image: 'maven:3.3.9-jdk-8-alpine', ttyEnabled: true, command: 'cat'),
                containerTemplate(name: 'curl', image: 'gcr.io/acn-devopsgcp/mc-image-curl:0.1', ttyEnabled: true, alwaysPullImage: true, command: 'cat'),
                containerTemplate(name: 'clair-scanner', image: 'gcr.io/acn-devopsgcp/mc-image-clairscanner:0.1', ttyEnabled: true, alwaysPullImage: true, command: 'cat'),
                containerTemplate(name: 'kubectl', image: 'gcr.io/acn-devopsgcp/mc-jenkinsslave:v1', ttyEnabled: true, command: 'cat'),
                containerTemplate(name: 'docker', image: 'gcr.io/google.com/cloudsdktool/cloud-sdk', ttyEnabled: true, command: 'cat')],
            volumes: [hostPathVolume(hostPath: '/var/run/docker.sock', mountPath: '/var/run/docker.sock'), secretVolume(mountPath: '/root/.kube', secretName: 'kube-config')])
{
node (label) {

    stage('Checkout Source') {
        git url:'https://github.com/koushikraghu/jenkinsdemo.git', branch:'test-deploy-stage'
      }
    stage('Deploy App') {
          kubernetesDeploy(configs: "nginx.yaml", kubeconfigId: "GkeDemoKubeConfig")
        }
      }

 }
