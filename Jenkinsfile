pipeline {
  agent any
  stages {
    stage('fetch') {
      environment {
        tenant_country = sh(script: 'git diff main origin/main --name-only "*.yml"' ,returnStdout: true).trim()
      }
      steps {
        sh 'git fetch --force'
        echo "${env.tenant_country}"
        script {
          datas = readYaml (file: "${env.tenant_country}")
        }

        echo datas.clusters.toString()
      }
    }

  }
}