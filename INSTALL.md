# Update Yum
sudo yum update -y

# Install Apache httpd
sudo yum install -y httpd
sudo systemctl start httpd
sudo systemctl enable httpd

# Install Docker
sudo amazon-linux-extras install docker -y &
sudo service docker start &
systemctl enable docker &
sudo usermod -a -G docker ec2-user &
sudo chmod 666 /var/run/docker.sock &

# Install kubectl
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl

# Install minikube
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
chmod +x minikube
sudo mv minikube /usr/local/bin/minikube

# Install git
yum install git -y
