node('docker') {
  checkout scm
  def ruby = docker.image('ruby:2.6.1')

  stage('Requirements') {
    ruby.inside {
      sh 'gem install bundler -v 2.0.1'
    }
  }

  stage('Build') {
    ruby.inside {
      sh 'bundle install'
    }
  }
  
  try {
    stage('Test') {
      ruby.inside {
        sh 'rake ci:all'
      }
    }
  } catch (e) {
    echo 'Tests have failed!'
  } finally {
    ruby.inside {
      junit 'test/reports/TEST-AppTest.xml'
    }
  }
}


