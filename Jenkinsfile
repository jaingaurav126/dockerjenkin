node {

    checkout scm

    docker.withRegistry('https://registry.hub.docker.com', 'jaingaurav126') {

        def customImage = docker.build("jaingaurav126/node-web-app")

        /* Push the container to the custom Registry */
        customImage.push()
    }
}
