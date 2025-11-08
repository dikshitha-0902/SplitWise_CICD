pipeline {
  agent any

  environment {
    NODE_HOME = "C:\Program Files\nodejs"     // adjust if Node.js is elsewhere
    PATH = "$NODE_HOME:$PATH"
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/dikshitha-0902/SplitWise_CICD.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'npm ci'
      }
    }

    stage('Lint') {
      steps {
        sh 'npm run lint || true'   // optional, skip if not configured
      }
    }

    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }

    stage('Deploy') {
      steps {
        // Example: copy built files to a deployment folder or web root
        sh '''
          DEPLOY_DIR=/var/www/vite-app
          sudo rm -rf $DEPLOY_DIR
          sudo mkdir -p $DEPLOY_DIR
          sudo cp -r dist/* $DEPLOY_DIR/
        '''
      }
    }
  }

  post {
    success {
      echo "✅ Pipeline completed successfully!"
    }
    failure {
      echo "❌ Pipeline failed. Check logs."
    }
  }
}
