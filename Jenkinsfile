node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

 //       app = docker.build("getintodevops/hellonode")
        app = docker.build("88915020/hello")
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        app.inside {
            sh 'echo "Tests passed"'
            //sh 'echo ${env.BUILD_NUMBER}'
            
        }
    }

    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
//        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            //docker.withRegistry('https://hub.docker.com/r/88915020/hellonode/', '704462d4-6f6f-4d31-b754-420659563d8c') {
          docker.withRegistry('https://hub.docker.com/r/', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
          //sh 'docker login -u 88915020 -p Ismail1988'    
          //sh 'docker login -u 88915020 -p Ismail1988'    
          
  //}
  }
  }


}
