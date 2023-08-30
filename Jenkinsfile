Node{
    stage('Build'){
        docker {
            image 'node:16-buster-slim' 
            args '-p 3000:3000' 
        }
    }
    stage('Test'){
        sh 'npm install'
    }
    stage('Deploy'){
        
    }
}