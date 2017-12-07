repositoryUrl = "https://github.com/contino/Getting-Started-With-Vault.git"
branch = "master"
packer_file = "packer/consul-vault.json"
pipeline {
  agent any
  stages {
    
    stage ('Checkout') {
        steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/contino/Getting-Started-With-Vault.git']]])
            sh ''' ls -al '''
        }
    }
     
     //load 'packer/consul-vault.json'
    stage ('Validate') {
        steps {
            
            print "Running packer validate on : ${packer_file}"
            sh '''cd packer
            packer validate consul-vault.json'''
        }
    }
      
    stage ('Build') {
        steps {
            sh '''cd packer
            packer build consul-vault.json'''
        }
         
    }
     
    stage ('Test') {
        steps {
            print "Testing goes here."
        }
    }
}
}
