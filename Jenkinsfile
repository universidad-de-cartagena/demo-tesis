pipeline {
  agent {
    label 'equipo01'
  }
  stages {
    stage('Docker huerfanos') {
      steps {
        sh 'docker container rm --force $(docker ps -a --quiet) || true'
        sh 'docker volume prune --force || true'
        sh 'docker image prune -f || true'
      }
    }
    stage('Imagen Docker') {
      steps {
        sh 'docker-compose build --force-rm'
      }
    }
    stage('Tests') {
      steps {
        sh 'docker-compose -f docker-compose.test.yml run -T --rm -e TEST_UID=$(id -u) -e TEST_GID=$(id -g) backend'
        script {
          publishHTML([
            allowMissing: false,
            alwaysLinkToLastBuild: true,
            keepAll: true,
            reportDir: 'reports/htmlcov/',
            reportFiles: 'index.html',
            reportName: 'Coverage report in HTML',
            reportTitles: ''
          ])
        }
        cobertura(coberturaReportFile: 'reports/coverage.xml', conditionalCoverageTargets: '70, 0, 0', lineCoverageTargets: '80, 0, 0', methodCoverageTargets: '80, 0, 0', sourceEncoding: 'ASCII')
        junit(testResults: 'reports/test_results/*.xml', allowEmptyResults: true)
        sh 'rm -rdf reports/'
      }
    }
    stage('Deploy') {
      steps {
        sh 'docker-compose up -d'
      }
      post {
        failure {
          sh 'docker volume prune --force || true'
          sh 'docker container rm --force $(docker ps -a --quiet) || true'
          sh 'docker image prune -f || true'
        }
      }
    }
  }
}
