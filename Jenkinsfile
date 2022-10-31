def imageName = 'mlabouardy/movies-parser'
def registry = 'https://registry.slowcoder.com'

node('workers'){
    stage('Checkout'){
        checkout scm
    }
    
    stage('Quality Tests'){
        def imageTest= docker.build("${imageName}-test", "-f Dockerfile.test .")
        imageTest.inside{
            sh 'golint'
        }
    }
    
    
    
    stage('Unit Tests'){
        imageTest.inside{
            sh 'go test'
        }
    }
}