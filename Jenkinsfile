pipeline{
    agent any
    environment{
        GITHUB_KEY = credentials('kalli')
    }
    stages{
        stage("testing"){
            steps{
                echo "testing now"
            }
        }
        stage("running"){
            steps{
                echo "testing now"
            }
        }

        stage("production"){
            steps{
                echo "Trying to get into Ec2 Instance..."
                sh  '''
                    sudo ssh -i /var/lib/jenkins/kalli.pem -t -o StrictHostKeyChecking=no ubuntu@ec2-13-40-216-111.eu-west-2.compute.amazonaws.com
                    sudo rm -rf node
                    sudo mkdir node
                    cd node
                    sudo git init
                    sudo git remote add origin https://$GITHUB_KEY_USR:$GITHUB_KEY_PSW@github.com/krates1/nodeJs.git
                    sudo git pull origin master
                    sudo npm install
                    sudo npm start
                    '''
            }
        }

    }
}
