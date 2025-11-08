pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/dikshitha-0902/SplitWise_CICD.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        bat 'npm install'
      }
    }

    stage('Run Application') {
      steps {
        echo "🚀 Starting Vite dev server..."
        bat '''
          start /b cmd /c "npm run dev > server.log 2>&1"
          timeout /t 5
          type server.log
        '''
      }
    }
  }

  post {
    success {
      echo "✅ Jenkins pipeline completed. App should be on http://localhost:5174"
    }
    failure {
      echo "❌ Pipeline failed. Check logs."
    }
  }
}
