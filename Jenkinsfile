pipeline {
    agent any

    stages {

	                stage('Build') {
                        steps {
                                sh 'mvn install'
                        }
                }

                stage('Unit Tests') {
                        steps {
                                sh 'mvn compiler:testCompile'
                                sh 'mvn surefire:test'
                                junit 'target/**/*.xml'
                        }
                }


                stage('Deployment') {
                        steps {
                                sh 'sshpass -p "gamut" scp target/gamutgurus.war gamut@172.17.0.4:/home/gamut/Distros/apache-tomcat-8.5.50/webapps'
                                sh 'sshpass -p "gamut" ssh gamut@172.17.0.4 "/home/gamut/Distros/apache-tomcat-8.5.50/bin/startup.sh"'
                }
                }
	}
    }
