node("docker") {
    docker.withRegistry('beanah/jenkins-hello-world-docker', 'beanah') {
    
        git url: "https://github.com/Turkeh/jenkins-hello-world.git", credentialsId: 'b6832ae9-e315-4952-8622-2b64bef2dd7d'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "your-project-name"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
