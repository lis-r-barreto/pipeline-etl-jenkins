pipeline {
    agent any

    environment {
        PYTHON_VERSION = '3.10'
    }

    parameters {
        booleanParam(name: 'EXTRACAO', defaultValue: true, description: 'Realizar extração de dados?')
        booleanParam(name: 'TRANSFORMACAO', defaultValue: true, description: 'Realizar transformação de dados?')
        booleanParam(name: 'CARREGAMENTO', defaultValue: true, description: 'Realizar carregamento de dados?')
        string(name: 'AMBIENTE', defaultValue: 'dev', description: 'Ambiente de execução')
    }

    options {
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds()
    }

    triggers {
        cron('H 23 * * 4')
    }

    stages {
        stage('Ambiente') {
            steps { 
                echo "Executando no ambiente: ${params.AMBIENTE}" 
            }
        }

        stage('Extrair Dados') {
            parallel {
                stage('Extrair Dados de Fonte A') {
                    when { expression { params.EXTRACAO } }
                    steps {
                        echo "Extraindo dados de Fonte A"
                        // Comandos para extração de dados da Fonte A
                    }
                }
                stage('Extrair Dados de Fonte B') {
                    when { expression { params.EXTRACAO } }
                    steps {
                        echo "Extraindo dados de Fonte B"
                        // Comandos para extração de dados da Fonte B
                    }
                }
            }
        }

        stage('Transformar Dados') {
            when { expression { params.TRANSFORMACAO } }
            steps {
                echo "Iniciando processo de transformação de dados."
                // Comandos para transformação de dados
            }
        }

        stage('Carregar Dados') {
            when { expression { params.CARREGAMENTO } }
            steps {
                echo "Iniciando processo de carregamento de dados."
                // Comandos para carregamento de dados
            }
        }

        stage('Validar Dados') {
            steps {
                echo "Validando dados carregados."
                // Comandos para validar os dados
            }
        }
    }

    post {
        always {
            cleanWs()
        }
        success {
            echo 'Pipeline ETL concluída com sucesso!'
        }
        failure {
            echo 'Pipeline ETL falhou!'
        }
    }
}
