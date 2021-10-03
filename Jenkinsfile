pipeline {
  agent any
  stages {
    stage('Dev Code Pull') {
      steps {
        echo 'Dev Code Pull'
      }
    }

    stage('Dev Maven Build') {
      steps {
        echo 'Dev Deploy'
      }
    }

    stage('QA Deploy') {
      steps {
        echo 'Deploy on QA'
      }
    }

    stage('QA Tests') {
      parallel {
        stage('QA Tests') {
          steps {
            echo 'UI Automation'
          }
        }

        stage('API ') {
          steps {
            echo 'API Automation'
          }
        }

        stage('Performance / Regression') {
          steps {
            echo 'Performance / Regression Tests'
          }
        }

      }
    }

    stage('QA Certify') {
      steps {
        input(message: 'Can we proceed to UAT?', ok: 'Yes')
      }
    }

    stage('UAT Deploy') {
      when {
        branch 'master'
      }
      steps {
        echo 'Deploy to UAT'
      }
    }

    stage('UAT Certify') {
      when {
        branch 'master'
      }
      steps {
        input(message: 'Can we proceed to Prod?', ok: 'Yes')
      }
    }

    stage('Prod Deploy') {
      when {
        branch 'master'
      }
      steps {
        echo 'Deploy to Production'
      }
    }

  }
}