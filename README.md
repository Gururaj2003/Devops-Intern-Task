clone this repo
add .env file
install docker and docker compose 
docker-compose up --build 
install ngnix
and start ngnix 
cd /etc/nginx/sites-available/default
add this proxy_pass http://127.0.0.1:8000 in location line
run docker and docker-compose build it


or else create a agent in jenkines and add this in pipeline 

pipeline {
    agent any

    stages {

        stage('Update System') {
            steps {
                sh  "sudo apt update"
        
            }
        }

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Gururaj2003/Devops-Intern-Task.git'
            }
        }

        stage('Install Docker') {
            steps {
                sh "
                  sudo apt install docker.io -y
                  sudo systemctl start docker
                  sudo systemctl enable docker"
            }
        }

        stage('Install Docker Compose') {
            steps {
                sh "
                  sudo apt install docker-compose -y
                "
            }
        }

        stage('Create .env file') {
            steps {
                sh "
                echo "SECRET_KEY=dev-secret-key" > .env
                echo "DEBUG=True" >> .env
                "
            }
        }

        stage('Install & Configure Nginx') {
            steps {
                sh "
                sudo apt install nginx -y

                sudo tee /etc/nginx/sites-available/default > /dev/null <<EOF
                server {
                    listen 80;
                    server_name _;

                    location / {
                        proxy_pass http://127.0.0.1:8000;
                    }
                }

                sudo nginx -t
                sudo systemctl restart nginx
                "
            }
        }

        stage('Run Docker Compose') {
            steps {
                sh "
                docker-compose up -d --build
                "
            }
        }

    }
}




and here are the cmd i used so for 
[
1  sudo apt update
    2  sudo apt install docker.io -y
    3  sudo systemctl start docker
    4  sudo systemctl enable docker
    5  sudo usermod -aG docker $USER
    6  logout
    7  sudo usermod -aG docker $USER
    8  sudo apt install git -y
    9  git clone https://github.com/Gururaj2003/Devops-Intern-Task.git
   10  cd Devops-Intern-Task
   11  ls
   12  cd ..
   13  ls
   14  cd Devops-Intern-Task/
   15  ls
   16  sudo apt update
   17  sudo apt install docker-compose -y
   18  docker-compose --version
   19  docker-compose up --build
   20  ls
   21  cd core/
   22  ls
   23  cat settings.py 
   24  sudo vim settings.py 
   25  docker-compose down
   26  docker-compose up --build
   27  cd ..
   28  ls
   29  ls -a
   30  cat .env.save 
   31  docker-compose down
   32  docker-compose up --build
   33  docker-compose up --build -d
   34  docker-compose logs django
   35  ls
   36  cd core/
   37  ls
   38  sudo vim settings.py 
   39  cd ..
   40  ls
   41  cat Dockerfile 
   42  sudo vim Dockerfile 
   43  docker-compose down
   44  docker-compose up --build
   45  docker-compose ps
   46  docker-compose up --build -d
   47  docker-compose ps
   48  docker ps 
   49  docker logs b29b973457db
   50  cat docker-compose.yml 
   51  sudo vim docker-compose.yml 
   52  docker-compose down
   53  docker-compose up --build
   54  sudo docker-compose down
   55  ls -a
   56  cat .env.save 
   57  sudo vim .env
   58  sudo docker-compose down
   59  sudo docker-compose up --build
   60  sudo apt update
   61  sudo apt install nginx -y
   62  sudo systemctl start nginx
   63  sudo systemctl enable nginx
   64  sudo systemctl start nginx
   65  sudo systemctl enable nginx
   66  sudo systemctl status nginx
   67  sudo sudo /etc/nginx/sites-available/default
   68  sudo /etc/nginx/sites-available/default
   69  sudo vim /etc/nginx/sites-available/default
   70  sudo nginx -t
   71  sudo systemctl restart nginx
   72  sudo vim /etc/nginx/sites-available/default
   73  sudo nginx -t
   74  sudo systemctl restart nginx
   75  sudo vim /etc/nginx/sites-available/default
   76  sudo nginx -t
   77  sudo systemctl restart nginx
   78  sudo vim /etc/nginx/sites-available/default
   79  cd Devops-Intern-Task/
   80  sudo docker-compose up --build
   81  sudo systemctl restart nginx
   82  sudo docker-compose up --build
   83  sudo apt update
   84  sudo apt install openjdk-17-jdk -y
   85  curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee   /usr/share/keyrings/jenkins-keyring.asc > /dev/null
   86  echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]   https://pkg.jenkins.io/debian-stable binary/ | sudo tee   /etc/apt/sources.list.d/jenkins.list > /dev/null
   87  sudo apt update
   88  sudo apt install jenkins -y
   89  sudo systemctl start jenkins
   90  sudo systemctl enable jenkins
   91  /var/lib/jenkins/secrets/initialAdminPassword
   92  sudo cat /var/lib/jenkins/secrets/initialAdminPassword
   93  ssh key-gen
   94  sudo ssh key-gen
   95  ssh-keygen
   96  cd ssh
   97  cd .ssh
   98  ls
   99  cd ..
  100  hostname -i
  101  cd .ssh
  102  ls
  103  sudo cat id_ed25519.pub 
  104  cai id_ed25519
  105  cat id_ed25519
  106  ssh ubussh ubu@65.2.79.120 
  107  ssh ubussh ubutu@65.2.79.120 
  108  ssh ubutu@65.2.79.120 
  109  sudo ssh ubutu@65.2.79.120 
  110  ssh -i key.pem ubuntu@65.2.79.120
  111  cd Devops-Intern-Task/
  112  sudo docker-compose up --build
  113  history
]



![IMG_9264](https://github.com/user-attachments/assets/e360f77e-a38c-4c48-b116-0b3427a6849f)





