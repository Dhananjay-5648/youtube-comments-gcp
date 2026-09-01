pipeline {
    agent any

    environment {
        PROJECT_ID = 'youtube-comments-507110'
    }

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

                stage('Run Sentiment Analysis') {
            steps {
                sh '''
                echo "Verifying credentials..."
                gcloud auth list
                echo "Setting GCP project..."
                gcloud config set project $PROJECT_ID
                echo "Running Ansible playbook..."
                ansible-playbook -i ansible/inventory ansible/playbooks/run_pretrained_sentiment.yml
                '''
            }
        }
