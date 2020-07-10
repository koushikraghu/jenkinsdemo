def label = "kubepod"
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
