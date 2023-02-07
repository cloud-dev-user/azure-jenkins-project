pipeline {
  agent {
    node {
      label 'azure-vm'
    }

  }
  stages {
    stage('build code ') {
      steps {
        sh 'mvn clean package &&  cp target/my-app.war .'
      }
    }
  
    stage('Create and push Docker image for sample app ') {
      steps {
        sh "  sudo docker build -t  ${docker_registry_name}:${tag_name} .  && sudo docker push ${docker_registry_name}:${tag_name}"
      }
    }

    stage('deployment using docker image ') {
      steps {
        sh "sudo docker run -d -p ${docker_port}:8080 --name sampleapp-${tag_name} ${docker_registry_name}:${tag_name}"
      }
    }

  }
  environment {
    docker_registry_name = 'vishnu11/sample-app'
   
  }
  parameters {
    string(name: 'tag_name', defaultValue: '', description: ' this is tag given to docker image')
    string(name: 'docker_port', defaultValue: '', description: ' this is post give to newly created docker container')
  }
}
