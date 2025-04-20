pipeline{

tools{
    maven 'mymaven'
}
agent any

stages{
    stage('Parallel Execution'){
        parallel{
             stage('Code Review'){
                steps{
                sh 'mvn pmd:pmd'
                 }
             }
             stage('Code Coverage'){
                steps{
                git 'https://github.com/Sonal0409/SonarQubeCoverageJava.git'
                sh 'mvn package'
            }
            post{
                always{
                    echo "Generating code coverage report..."
                }
                success{
                  recordCoverage(tools: [[parser: 'JACOCO']])
                }
            }

             }


        }
    }
}

}
