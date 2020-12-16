@Library('shared-library') _

pipeline {
    options {
        ansiColor('xterm')
        timestamps()
    }
    agent {
        label 'docker-slave-java'
    }

    stages {
        stage('test测试') {
            when {}
            steps {
              
                script {
                    println "import shared-library"
                    result = helloworld 'test'
                    println result
                }
            }
        }
    post {
        unstable {
            emailext (
                body: """项目名称：${JOB_NAME}\n构建编号：${BUILD_NUMBER}\n构建日志：${BUILD_URL}console""",
                subject: '【Jenkins构建通知】:$JOB_NAME - Build # $BUILD_NUMBER - Unstable!',
                to: 'test@aa.cn',
                from: 'jenkins@aa.cn'
            )   
        }   
        success {
            emailext (
                body: """项目名称：${JOB_NAME}\n构建编号：${BUILD_NUMBER}\n构建日志：${BUILD_URL}console""",
                subject: '【Jenkins构建通知】:$JOB_NAME - Build # $BUILD_NUMBER - Successful!',
                to: 'test@aa.cn',
                from: 'jenkins@aa.cn'
            )   
        }   
        failure {
            emailext (
                body: """项目名称：${JOB_NAME}\n构建编号：${BUILD_NUMBER}\n构建日志：${BUILD_URL}console""",
                subject: '【Jenkins构建通知】:$JOB_NAME - Build # $BUILD_NUMBER - Failure!',
                to: 'test@aa.cn',
                from: 'jenkins@aa.cn'
            )   
        }   
    }
  }
