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
        // Start the dev server and open in browser
        bat '''
          start cmd /c "npm run dev"
          timeout /t 8 >nul
          start http://localhost:5174
        '''
      }
    }
  }

  post {
    success {
      echo "✅ Dev server started and browser opened!"
    }
    failure {
      echo "❌ Something went wrong. Check logs."
    }
  }
}
