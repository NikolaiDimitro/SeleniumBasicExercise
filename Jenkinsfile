pipeline {

    agent any

    stages {

        stage("Dependency Restore") {
            steps {
                bat "dotnet restore"
            }
            post {
                success {
                    echo "Restore succeeded"
                }
                failure {
                    echo "Restore failed"
                }
            }
        }

        stage("Build") {
            steps {
                bat "dotnet build"
            }
            post {
                success {
                    echo "Build succeeded"
                }
                failure {
                    echo "Build failed"
                }
            }
        }

        stage("Test") {
            parallel {

                stage("Run test for Project 1") {
                    steps {
                        bat 'dotnet test TestProject1/TestProject1.csproj --no-build --verbosity normal'
                    }
                    post {
                        success {
                            echo "Test 1 succeeded"
                        }
                        failure {
                            echo "Test 1 failed"
                        }
                    }
                }

                stage("Run test for Project 2") {
                    steps {
                        bat 'dotnet test TestProject2/TestProject2.csproj --no-build --verbosity normal'
                    }
                    post {
                        success {
                            echo "Test 2 succeeded"
                        }
                        failure {
                            echo "Test 2 failed"
                        }
                    }
                }

                stage("Run test for Project 3") {
                    steps {
                        bat 'dotnet test TestProject3/TestProject3.csproj --no-build --verbosity normal'
                    }
                    post {
                        success {
                            echo "Test 3 succeeded"
                        }
                        failure {
                            echo "Test 3 failed"
                        }
                    }
                }
            }
        }
    }
}
