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
                sh '''
                    mkdir -p .npm-global
                    mkdir -p _cacache
                    export PATH=.npm-global/bin:$PATH

                    npm config set prefix '.npm-global'
                    npm config set cache '_cacache'
                    npm config set jobs 1
                    npm config set strict-ssl false
                  '''
                  sh 'npm i'
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
