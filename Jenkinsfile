node {

    checkout scm

    docker.withRegistry('https://registry.hub.docker.com', '13a9cff4-2785-426d-a5ce-149776209121') {

        def customImage = docker.build("jaingaurav126/node-web-app")

        /* Push the container to the custom Registry */
        customImage.push()
    }
}
