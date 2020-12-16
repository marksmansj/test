@Library('shared-library') _

pipeline {
    agent {
        label 'slave-${UUID.randomUUID().toString()}'
    }

    stages {
        stage('test测试') {
            steps {
              
                script {
                    println "import shared-library"
                    result = helloworld 'test'
                    println result
                }
            }
        }
  }
}
