# Docker_connection_with_MYSQL
## Docker connection with database (mysql & phpmyadmin)
<ol>
To store data in a database we need <strong>MySQL database </strong>, so now we gonna start study about  <strong>MySQL database </strong> with docker. For visualization we will use  <strong>PHPMyAdmin </strong></br>
 <strong>MySQL </strong> is a widely used, open-source relational database management system (RDBMS).</li>


### We need to download mysql image in our system
<ol>
<li> <strong>Pull MySql image </strong> from docker hub. Following command will pull the latest mysql image.</br>
 <strong>$ docker pull mysql:latest </strong></li> 
 
 ![docker_pull](https://user-images.githubusercontent.com/47202519/56024620-00836280-5d2e-11e9-9576-09536c5ce12d.png)

<li>Check docker status </br>
 <strong>$ service mysql status </strong></li>  
 
 ![docker_status](https://user-images.githubusercontent.com/47202519/56024691-2f99d400-5d2e-11e9-8baa-35dfdcf7d9ac.png)


<li>Run a container from this image.  <strong>‘-name’ </strong> gives a name to the container.  <strong>‘ -e’ </strong> specifies run time variables you need to set. Set the password for the MySQL root user using  <strong>‘MYSQL_ROOT_PASSWORD’= "password" </strong>.  <strong>‘-d’ </strong> tells the docker to run the container in background.</br>
<strong>$ docker run --name mysql -e MYSQL_ROOT_PASSWORD=Server@123 -d mysql:5.7</strong></li>  

![docker_run](https://user-images.githubusercontent.com/47202519/56024822-7091e880-5d2e-11e9-9a9f-78be02346a62.png)


<li>Then check the status of the container</br>
Now you should be able to see that MySQL is running on port <strong>3306</strong>.</br>
<strong>$ docker ps -a</strong></li>  
</ol>



### MAKE CONNECTION WITH MYSQL
<ol>
<li>To enter in <strong>MYSQL</strong> use <strong>CONTAINER_ID</strong></br>
<strong>$ docker exec -it 0738822bc24f  bash</strong></li> 

<li>Now ROOT@CONTAINER_ID  need a path to make a access in mysql </br>
<strong>root@0738822bc24f:/# mysql -u root -p</strong></li>  

![exec](https://user-images.githubusercontent.com/47202519/56024992-e1d19b80-5d2e-11e9-8e3b-b9922999728f.png)

<li>Create database</li>
<ol>
<li><strong>mysql> show databases;</strong></li>  
  
![show_db](https://user-images.githubusercontent.com/47202519/56025135-23fadd00-5d2f-11e9-9ee7-88e2011c8a99.png)
 
<li><strong>mysql> create database first;</strong></li>
<li><strong>mysql> show databases;</strong></li> 

![create_db](https://user-images.githubusercontent.com/47202519/56025155-2b21eb00-5d2f-11e9-9c8d-7e07a05bc07d.png)

<li><strong>exit;</strong> to go back </li>
</ol>
</ol>


### Accessing MySQL through a Web Interface.
<ol/>
<strong>phpMyAdmin</strong> gives us a web interface to access <strong>MySQL database</strong> and we are going to use that to access and administer MySQL database that we have set up earlier.</br>

<li>Pull phpMyAdmin image from docker hub</br>
<strong>$ docker pull phpmyadmin/phpmyadmin</strong></li>  

![pull_admin](https://user-images.githubusercontent.com/47202519/56025545-f5313680-5d2f-11e9-9cf3-93458080cc28.png)

<li>Now create a link with phpmyadmin, <strong>--link= running MYSQL container</strong></br>
<strong>$ docker run --name test-phpmyadmin -d --link mysql:db -p 8081:80 phpmyadmin/phpmyadmin</strong></li>  

![run_admin](https://user-images.githubusercontent.com/47202519/56025924-c798bd00-5d30-11e9-8803-f0176512f6cd.png)

<li>Now we need to run <strong>port=0.0.0.0:8081</strong> of running <strong>image=phpmyadmin/phpmyadmin</strong> and run in a browser</li>  

![phpmy](https://user-images.githubusercontent.com/47202519/56025966-d8493300-5d30-11e9-8eaf-28ddb10e70ad.png)

<li>Enter the password of that we set for mysql.</li>
<li>Now we can view the same database that we created in <strong>docker MYSQL</strong> </li>
</ol>
</ol>
