# How to Run MySQL Container with a Volume Attached
Use the following command:
docker run --name mysql-container -d -p 3306:3306 -v my-sql-data:/var/lib/mysql mysql-local:1.0.0

# How to run an App container which will connect to a MySQL db container
1. Find MySQL container IP:
docker inspect mysql-container | grep "IPAddress"
2. Update file todolist -> settings.py line 83(set HOST to the MySQL container's IP which you received in step 1)
3. Run an App container
docker run -d --name app -p 8080:8080 todoapp:2.0.0
the application will be available in the browser
http://localhost:8080

# Docker hub 
https://hub.docker.com/repository/docker/vitaliiog/todoapp/tags/2.0.0/sha256-a83a78057ba8c72210878d9e73df3c0509f839a626664692d04b0eadaad5dca8
https://hub.docker.com/repository/docker/vitaliiog/mysql-local/tags/1.0.0/sha256-5d7d1891f1f816e24ca3064f147589dbf9146ff159333dc2bff50d4edd962c23

# How to access the application via a browser
Main App: http://localhost:8080
API: http://localhost:8080/api/