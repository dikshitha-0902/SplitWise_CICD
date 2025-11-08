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

    stage('Build') {
      steps {
        bat 'npm run build'
      }
    }

    stage('Run Application') {
      steps {
        // start the app in a new background window
        bat 'start cmd /c "npm start"'
      }
    }
  }

  post {
    success {
      echo "✅ Application started successfully!"
    }
    failure {
      echo "❌ Build failed. Check logs."
    }
  }
}
