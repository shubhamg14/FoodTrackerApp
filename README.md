# FoodTrackerApp
A food tracking application created using Flask and deployed in Amazon Lightsail.

Following main features of the application:
1. Can be used to add new food items to the databases.
2. New dates can be added to the database and then different food items consumend on that day can be added.
3. Total calorie count consumed for each day shown on the home screen.

## Features

### Home Screen

1. The new date for which food has to be tracked can be added
2. Can be used to add new food items.

![alt text](https://github.com/shubhamg14/FoodTrackerApp/blob/master/images/food-app-home-1.PNG)

![alt text](https://github.com/shubhamg14/FoodTrackerApp/blob/master/images/food-app-home-2.PNG)

### Add New Food Item

1. Can be navigated through Home Page and can be used to add new food item to the database.

![alt text](https://github.com/shubhamg14/FoodTrackerApp/blob/master/images/food-app-add-food.PNG)


### Adding food for new date

1. On Home page, new date can be aded and then food items eaten on that day can be selected
2. Total calorie count consumed that day would be reflected on the Home screen.


![alt text](https://github.com/shubhamg14/FoodTrackerApp/blob/master/images/food-app-date-details-1.PNG)
![alt text](https://github.com/shubhamg14/FoodTrackerApp/blob/master/images/food-app-date-details-2.PNG)

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
 17. Copy code into Amazon Lightsail using Winscp or Clone git repository
 18. Update database path to '/home/ubuntu/your-project-folder'
 19. Start app using command "gunicorn app:app"
