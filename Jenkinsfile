pipeline{
    agent any
    environment{
        GITHUB_KEY = credentials('shemmy')
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
                    sudo ssh -i /var/lib/jenkins/shemmy.pem -t -o StrictHostKeyChecking=no ubuntu@ec2-18-134-155-120.eu-west-2.compute.amazonaws.com
                    cd /var/www
                    sudo rm -rf html
                    sudo mkdir html
                    cd html
                    sudo git init
                    sudo git remote add origin https://$GITHUB_KEY_USR:$GITHUB_KEY_PSW@github.com/krates1/metal.git
                    sudo git pull origin master
                    '''
            }
        }

    }
}
