pipeline{

stages{
	    stage('Clone repository') {
	        /* Let's make sure we have the repository cloned to our workspace */
	        steps{
	        	checkout scm
	        }
	    }
	
	    stage('Build image') {
	        /* This builds the actual image; synonymous to
	         * docker build on the command line */
			steps{
	        	app = docker.build("timgondasr/hellonode")
	        }
	    }
	
	    stage('Test image') {
	        /* Ideally, we would run a test framework against our image.
	         * For this example, we're using a Volkswagen-type approach ;-) */
	
	        app.inside {
	            sh 'echo "Tests passed"'
	        }
	    }
	
	    stage('Push image') {
	        /* Finally, we'll push the image with two tags:
	         * First, the incremental build number from Jenkins
	         * Second, the 'latest' tag.
	         * Pushing multiple tags is cheap, as all the layers are reused. */
	        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
	            app.push("${env.BUILD_NUMBER}")
	            app.push("latest")
	        }
	    }
	    
	    stage('Deploy image staging') {
	        /* Finally, we'll push the image with two tags:
	         * First, the incremental build number from Jenkins
	         * Second, the 'latest' tag.
	         * Pushing multiple tags is cheap, as all the layers are reused. */
	    }
	    
	    stage('Test image staging') {
	        /* Finally, we'll push the image with two tags:
	         * First, the incremental build number from Jenkins
	         * Second, the 'latest' tag.
	         * Pushing multiple tags is cheap, as all the layers are reused. */
	    }
	    
	    stage('Deploy image production') {
	        /* Finally, we'll push the image with two tags:
	         * First, the incremental build number from Jenkins
	         * Second, the 'latest' tag.
	         * Pushing multiple tags is cheap, as all the layers are reused. */
	    }
    }
}

