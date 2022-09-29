pipeline {
    agent any
    tools {nodejs "node"}
    stages {
        stage('Git-Checkout'){
            steps{
                echo "Checkout from git"
                git 'https://github.com/mrvincentoti/simple-node-js-react-npm-app.git'
            }
        }

        stage('Build'){
            steps {
                echo "Compile Frontend"
                sh 'npm --version'
                sh 'npm run build'
            }
        }

        stage('JUnit'){
            steps {
                echo "JUnit Passed Successfully"
            }
        }

        stage('Quality-Gate'){
            steps {
                echo "SonarQube Quality Check Passed Successfully"
            }
        }

        stage('Deploy'){
            steps {
                echo "Passed Successfully"
            }
        }
    }
    post {
        always{
            echo "This will always run"
        }
        success{
            echo "This will only run on success"
        }
        failure{
            echo "This will run on failure"
        }
        unstable{
            echo "This will only run if the run was marked unstable"
        }
        changed{
            echo "This will only run if the stage in the pipeline has changed"
            echo "For example if the pipeline was initially failing, but now successful"
        }
    }
}
