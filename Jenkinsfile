def label = "kubepod"
def serviceaccount = "jenkins-admin"
podTemplate(label: label, serviceAccount: serviceaccount,imagePullSecrets: ['amrutha'],
            containers: [
                containerTemplate(name: 'python', image: 'python:3-alpine', ttyEnabled: true, command: 'cat')])
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
