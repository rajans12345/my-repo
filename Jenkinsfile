pipeline {
    
    agent {
        
        label {
            
            label 'built-in'
            customWorkspace '/mnt/rajan'
        }
    }
    stages {
        
        stage ('start docker') {
            
            steps {
                
                sh "systemctl start docker"
            }
        }
        stage ('Delete unused images & stop containers') {
            
            steps {
                
                dir ('/mnt') {
                
                sh "docker system prune -a -f"
                
                }
            }
        }
        stage ('Run services in Docker-compose.yaml file') {
            
            steps {
                
                dir ('/mnt') {
                    
                    sh "docker-compose up -d"
                }
            }
        }
        stage ('View stop & running services') {
            
            steps {
                
                dir ('/mnt') {
                    
                    sh "docker-compose ps -a"
                }
            }
        }
    }
}
