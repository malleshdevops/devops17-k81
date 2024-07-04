// remote backend system
pipeline {
    agent any

    stages {
        stage('select k8') {
            steps {
              sh 'kubectl config use-context arn:aws:eks:us-west-2:897276212041:cluster/devops17-eks-57JbjgBf'    
            
        }
        }
        stage('connect k8') {
            steps {
                sh '''
                  kubectl get nodes
                  #if [ $? == 0 ]
                  #then
                  #{
                   # echo "sucessfully connected to cluster"
                  #}
                  #else{
                  # echo "unable to connect to cluster"
                   #exit 1
                  #}
                  
                '''
            }
        }
        stage('deploy k8 files') {
            steps {
                
              sh '''
                          kubectl apply -f $WORKSPACE/deploy.yaml
              '''
                
            }
        }
        stage('validate deployment') {
            steps {
                sh '''
                 kubectl get po
                 #if [ $? == 0 ]
                 #then
                 #{
                 #  echo "sucessfully connected to cluster"
                  #}
                  #else{
                   #echo "unable to connect to cluster"
                   #exit 1
                  #}
                '''
            }
        }
    }
}
