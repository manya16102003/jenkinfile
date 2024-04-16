pipeline {
    agent any
    
    // Using the 'NodeJS' tool from the Jenkins Global Tool Configuration
    tools {
        nodejs 'NodeJS'
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Automatically performed by Jenkins
                echo 'Checking out the code...'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                // This will install both the devDependencies and dependencies from your package.json
                sh 'npm install'
            }
        }
        
        stage('Build') {
            steps {
                // This will run the TypeScript compiler and then Vite build according to your build script
                sh 'npm run build'
            }
        }
        
        // You don't have a test script in package.json. If you add one, you can uncomment this.
        // stage('Run Tests') {
        //     steps {
        //         // Run the test script here
        //         sh 'npm test'
        //     }
        // }
        
        stage('Preview') {
            steps {
                timeout(time: 5, unit: 'MINUTES') { // Adjust the time as needed
                    sh 'npm run preview &'
                }
            }
        }
        
        // Include your deployment stage here
        // stage('Deploy') {
        //     steps {
        //         // Add your deployment commands here
        //         sh '<deployment_command>'
        //     }
        // }
    }
    
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'Build was successful.'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
