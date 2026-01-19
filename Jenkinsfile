pipeline{
        agent any

        stages{
                stage("Clone Repo")
                {
                        steps
                        {
                                git branch: 'main',
                                url: 'https://github.com/Sohailsaifi-aws/python-docker-jenkins.git'
                        }
                }
                stage("Build Docker Image")
                {
                        steps{
                                sh 'docker build -t python-docker-jenkins .'
                        }
                }
                stage("Stop Old Container"){
                        steps{
                        sh '''
                                docker stop  $(docker ps -q)
                                docker rm -f $(docker ps -aq)
                        '''
                        }
                }
                stage("Docker Container Run"){
                        steps{
                                sh '''
                                        docker run -d --name python-docker - 5000:5000 python-docker-jenkins
                                '''

                        }
                }
        }
}
