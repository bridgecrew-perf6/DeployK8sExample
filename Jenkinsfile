pipeline {
  agent any
  
    parameters {
  	choice choices: ['qa', 'production'], description: 'Select namespace for deployment', name: 'DEPLOY_TO' 
  	string(name: 'IMAGE_TAG', description: 'docker image tag')
   }

  
  environment {
  	MY_KUBECONFIG = credentials('k8sconfig')
  }
  
  stages {
    stage('Deploy K8s') {
      steps {
      	//replace image tag in application.yaml file
      	sh "kubectl apply --kubeconfig ${MY_KUBECONFIG} -f application.yaml -n ${DEPLOY_TO}"
      }
    }
  }
}
