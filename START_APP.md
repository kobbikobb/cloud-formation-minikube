# Clone and run a sample application
cd /home/ec2-user
git clone https://github.com/kobbikobb/guessthename.git

# Start minikube
minikube start
minikube addons enable ingress

# Deploy sample application
cd guessthename
./k8s/deploy.sh

# Edit httpd to provide a reverse proxy
INGRESS_IP="$(kubectl get ingress | grep -o '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}')"

sudo bash -c "echo 'LoadModule proxy_module modules/mod_proxy.so
<VirtualHost *:80>
    ProxyPass / http://$INGRESS_IP/
    ProxyPassReverse / http://$INGRESS_IP/
</VirtualHost>' >> /etc/httpd/conf/httpd.conf"

sudo systemctl restart httpd

