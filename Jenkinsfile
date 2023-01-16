pipeline{
    agent {
        docker {
            // image 'allbears/jenkins-android:1.0.1'
            image 'cmii/android-build:1.0.0'
            // 共享Gradle下载缓存，使构建任务执行更快
            args '-v $HOME/.gradle:/root/.gradle'
        }
    }
    stages {
        stage('Build'){
            steps {
                sh './gradlew clean assembleDebug --no-daemon'
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'app/build/outputs/**/*.apk', fingerprint: true
            }
        }
    }
}
