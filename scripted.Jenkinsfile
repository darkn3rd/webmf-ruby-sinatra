node {
  checkout scm
  def ruby = docker.image('ruby:2.6.1')

  ruby.image('ruby:2.6.1').inside {
    stage('Requirements') {
      sh 'gem install bundler -v 2.0.1'
    }

    stage('Build') {
      sh 'bundle install'
    }
    
    try {
      stage('Test') {
        sh 'rake ci:all'
      }
    } catch (e) {
      echo 'Tests have failed!'
    } finally {
        junit 'test/reports/TEST-AppTest.xml'
    }
  }
}


