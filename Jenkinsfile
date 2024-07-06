pipeline {
    agent any

    stages {
        stage('Clone-Repo') {
	    	steps {
	        	git 'https://github.com/swathich29/gamutkart.war'
	    	}
        }
	stage('Build') {
		steps {
			sh 'mvn install'
		}
	}	
 
	stage ('Compile'){
	        steps {
			sh 'mvn clean compile'
                }
	}

	stage('Run Tests') {
	    steps {
	       sh 'mvn test'
	    }
	}

        stage('Package as WAR') {
            steps {
                sh 'mvn package'
            }
        }
	stage('Deployment') {
	   steps {
		sh 'scp target/gamutkart.war root@172.31.37.162://root/apache-tomcat-9.0.90/webapps'
	}
    }
}
}
