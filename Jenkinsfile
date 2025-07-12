pipeline {
  agent any
  stages {
    stage('Install Dependencies') {
      steps {
        sh '''
                    sudo apt-get update
                    sudo apt-get install -y build-essential cmake g++ mingw-w64
                '''
      }
    }

    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build for Linux') {
      steps {
        sh '''
                    cmake -S . -B $BUILD_DIR/linux
                    cmake --build $BUILD_DIR/linux
                '''
      }
    }

    stage('Build for Windows (Cross-Compile)') {
      steps {
        sh '''
                    cmake -S . -B $BUILD_DIR/windows -DCMAKE_TOOLCHAIN_FILE=./toolchains/mingw.cmake
                    cmake --build $BUILD_DIR/windows
                '''
      }
    }

  }
  environment {
    BUILD_DIR = 'build'
  }
}