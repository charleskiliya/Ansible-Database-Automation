pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Récupérer le code source depuis le référentiel Git
                git 'https://github.com/charleskiliya/Ansible-Database-Automation.git'
            }
        }

        stage('Build') {
            steps {
                // Installer les dépendances nécessaires
                sh 'ansible-playbook -i inventory deploy-docker.yml'
            }
        }

        stage('Test') {
            steps {
                // Exécuter les tests sur le système de gestion automatique de la base de données
                sh 'ansible-playbook -i inventory.ini database_tests.yml'
            }
        }

        stage('Deploiement') {
            steps {
                // Exécuter les tâches Ansible pour la gestion automatique de la base de données
                sh 'ansible-playbook -i inventory deploy-database.yml'
            }
        }

        stage('Enregistrer les config') {
            steps {
                // Enregistrer les configurations
                sh 'ansible-playbook -i inventory cleanup.yml'
            }
        }
    }
}

