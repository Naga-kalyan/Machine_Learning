<h1 align="center">Banglore House Price Prediction</h1>
<div align="center">
<img src="https://github.com/Naga-kalyan/Machine_Learning/blob/master/END-TO-END-ML/BangloreHousePricePrediction/Imgs/bhp.gif">
</div>

Build a real estate price prediction website.First build a model using sklearn and linear regression using banglore home prices dataset from kaggle.com. Second step would be to write a python flask server that uses the saved model to serve http requests. Third component is the website built in html, css and javascript that allows user to enter home square ft area, bedrooms etc and it will call python flask server to retrieve the predicted price. During model building we will cover almost all data science concepts such as data load and cleaning, outlier detection and removal, feature engineering, dimensionality reduction, gridsearchcv for hyperparameter tunning, k fold cross validation etc. Technology and tools wise this project covers,

1. Numpy and Pandas for data cleaning
2. Matplotlib for data visualization
3. Sklearn for model building
4. Python flask for http server
5. AWS for model deployment

<h1>Steps for Model deployment</h1>

1. Create EC2 instance in AWS and allow HTTP incoming traffic.
2. Now connect to instance using git
<br>&emsp;&emsp; ssh -i "Downloads\abc.pem" ubuntu@ec2-54-235-58-149.compute-1.amazonaws.com
3. nginx setup
<br>&emsp;  i. Install nginx on instance using following commands
```
sudo apt-get update
sudo apt-get install nginx 
```
<br>&emsp;  ii. Check status of nginx using
```
sudo service nginx status
```
<br>&emsp; iii. Here are the commands to start/stop/restart nginx
```
sudo service nginx start
sudo service nginx stop
sudo service nginx restart
```
<br>&emsp; iv. Now when u load url ec2-54-197-168-153.compute-1.amazonaws.com we will see a message saying "welcome to nginx" This means your nginx is setup and running.
4. Now copy all files to instance befault loaction /home/ubuntu using Winscp.
5. After copying code on EC2 server now we can point nginx to load our property website by default. For below steps
<br>&emsp;  i. Remove symlink for default file in /etc/nginx/sites-enabled directory
```
sudo unlink default
```
<br>&emsp;  ii. Create this file /etc/nginx/sites-available/bhp.conf. The file content looks like this
```
server {
    listen 80;
        server_name bhp;
        root /home/ubuntu/BangloreHousePricePrediction/Client;
        index app.html;
        location /api/ {
             rewrite ^/api(.*) $1 break;
             proxy_pass http://127.0.0.1:5000;
        }
}
```
<br>&emsp;  iii. Create symlink for this file in /etc/nginx/sites-enabled by running this command
```
sudo ln -v -s /etc/nginx/sites-available/bhp.conf
```
<br>&emsp;  iv. Restart nginx
```
sudo service nginx restart
```
6. Now install python packages and start flask server
```
sudo apt-get install python3-pip
pip install flask
pip install numpy
pip install sklearn
python3 /home/ubuntu/BangloreHousePricePrediction/client/server.py
```
7. Now just load your cloud url in browser (for me it was http://ec2-54-197-168-153.compute-1.amazonaws.com/) and this will be fully functional website running in production cloud environment
