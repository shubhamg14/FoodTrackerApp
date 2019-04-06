# FoodTrackerApp
A food tracking application created using Flask and deployed in Amazon Lightsail.

This application takes in input from the user for foods eaten in a day and accordingly outputs the total number of calories consumed by the user in a day.




## Deploying the Application on Amazon Lightsail

### Setting up instance on Amazon Lightsail

1. Create a login on AWS and select Amazon Lightsail
2. Click create instance
3. Select Nginx and use Ubuntu and click create instance
4. Open instance and type first command "sudo apt-get update"
5. Install Nginx "sudo apt-get install nginx"
6. Start Nginx "sudo /etc/init.d/nginx start"
7. Remove default file from Nginx "sudo rm /etc/nginx/sites-enabled/default"
8. Create Nignx file "sudo touch /etc/nginx/sites-available/flask_settings"
9. Create a link between sites-available and sites-enabled files "sudo ln -s /etc/nginx/sites-available/flask_settings /etc/nginx/sites-enabled/flask_settings"
10. Configure flask_settings file under sites-enabled "sudo vi /etc/nginx/sites-enabled/flask_settings"

          server {
                  location / {
                          proxy_pass http://127.0.0.1:8000;
                          proxy_set_header Host $host;
                          proxy_set_header X-Real -IP $remote_addr;
                 }
          }
 
 11. Restart the server "sudo /etc/init.d/nginx restart"
 12. Install python3 and pip "sudo apt-get install python3-pip"
 13. Install virtual environment "sudo pip install virtualenv"
 14. Create a virtual environment "virtualenv env"
 15. Activate virtual environment "source env/bin/activate"
 16. Install Flask and Gunicorn(Application server) "pip install flask gunicorn"
