// Instead of annotating an unnecessary import statement, the symbol _ is annotated, according to the annotation pattern.
@Library('adop-pluggable-scm-jenkinsfile') _

def repoName = "spring-petclinic"
def regRepo = "adop-cartridge-java-regression-tests"

pipeline {
    agent { label 'java8' }
    environment{
        // Sonar Project Info - You must replace these vars with the Project Name and Key from the ADOP Portal!
        SONAR_PROJECT_NAME = 'Simple Java project analyzed with the SonarQube Runner'
        SONAR_PROJECT_KEY = 'java-sonar-runner-simple'
        ENVIRONMENT_NAME = 'CI'
        }
    stages{
        stage("Reference Application Build"){
            steps{
                echo 'Compiling...'
                deleteDir()
                checkout scm
                withMaven(maven: 'ADOP Maven') {
                    sh 'mvn clean install'   //sustitye aqui el comando maven
                }
            }
        }
        stage("Reference Application Unit Tests"){
            steps{
                echo 'Testing...'
                withMaven(maven: 'ADOP Maven') {
                    sh "mvn test"
                }
            }  
        } 
    }
}