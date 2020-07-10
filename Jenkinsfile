label = "kubepod"
{
  node(label){
    stage('Checkout Source') {
        git url:'https://github.com/justmeandopensource/playjenkins.git', branch:'test-deploy-stage'
      }
    stage('Deploy App') {
          kubernetesDeploy(configs: "nginx.yaml", kubeconfigId: "GkeDemoKubeConfig")
        }
      }

  }
