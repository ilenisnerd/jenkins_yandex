pipeline {
    agent any

    parameters {
        // Boolean параметр, нужно ли запускать тесты после сборки?
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Should tests be executed?')

        // String параметр для задания версии приложения
        string(name: 'APP_VERSION', defaultValue: '1.0.0', description: 'Version of the application to deploy')

        // Choice параметр для выбора платформы, для которой происходит сборка
        choice(name: 'BUILD_PLATFORM', choices: ['Windows', 'Linux', 'Darvin'], description: 'Build platform')
    }

    stages {
        stage('Build') {
            steps {
                echo "Building application version: ${params.APP_VERSION} for ${params.BUILD_PLATFORM} platform"
                // Здесь могут быть команды сборки для каждой из платформ:
                script {
                    // В зависимости от параметра будут выполняться нужные шаги
                    if (params.BUILD_PLATFORM == 'Windows') {
                        echo 'Executing build for Windows...'
                        // Команды для сборки под Windows
                    } else if (params.BUILD_PLATFORM == 'Linux') {
                        echo 'Executing build for Linux...'
                        // Команды для сборки под Linux
                    } else if (params.BUILD_PLATFORM == 'macOS') {
                        echo 'Executing build for macOS...'
                        // Команды для сборки под macOS
                    }
                }
            }
        }

        stage('Test') {
            // Стейдж запустится, только если 
            when {
                expression { return params.RUN_TESTS }
            }
            steps {
                echo "Running tests..."
                // Запуск тестов
            }
        }

        stage('Upload to registry') {
            steps {
                echo "Upload to registry version: ${params.APP_VERSION}."
                // Загрузка собранного бинарного файла в хранилище
            }
        }
    }
}