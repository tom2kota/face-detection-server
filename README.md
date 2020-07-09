# Face detection API - Server (Dockerized) with [Client](https://github.com/tom2kota/face-detection-server)


```
npm i

npm audit fix

npm start
```

```
sudo docker-compose up --build

sudo docker-compose up

sudo docker-compose ps
sudo docker stop

sudo docker-compose down
```

 --------------------

 
- Make sure you have docker installed and running on your computer

- Run `sudo docker-compose up` ( you may have to run `sudo docker-compose up --build` for the first setup phase)

- You must add your own [API key](https://portal.clarifai.com/apps/) in the `controllers/image.js` file to connect to Clarifai API.

- You will also need to update Line 22 in server.js to your client app port (i.e. 3001)


**Important:** if you are getting conflict errors, you should run `sudo docker stop <container name>` 
that is already running in the background.

**Important:** if you are getting other errors, you should run `sudo docker-compose down` to bring everything down, and start over.

To access backend's bash:
```
sudo docker-compose exec smart-brain-api bash
```

To access postgres: (adjust PORT number if needed)
```
psql postgres://<username>:<password>@localhost:5432/smart-brain
```


``` 
psql postgres://admin:password@localhost:5432/smart-brain
```

To access redis:
```
sudo docker-compose exec redis redis-cli
```

You can grab Clarifai API key [here](https://www.clarifai.com/)


** Make sure you use postgreSQL instead of mySQL for this code base.


-------------
log:
```  
postgres           | Success. You can now start the database server using:
postgres           |     pg_ctl -D /var/lib/postgresql/data -l logfile start
postgres           | server started
backend            | app is running on port 3000
postgres           | server stopped
postgres           | 
postgres           | PostgreSQL init process complete; ready for start up.
postgres           | 
postgres           | 2020-07-08 11:17:11.628 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
postgres           | 2020-07-08 11:17:11.631 UTC [1] LOG:  listening on IPv6 address "::", port 5432
postgres           | 2020-07-08 11:17:11.827 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
postgres           | 2020-07-08 11:17:12.121 UTC [74] LOG:  database system was shut down at 2020-07-08 11:17:10 UTC
postgres           | 2020-07-08 11:17:12.228 UTC [1] LOG:  database system is ready to accept connections


```

---------------


## curl


[localhost:3000](http://localhost:3000/)


[localhost:3000/register](http://localhost:3000/register)
``` 
curl -X POST -d '{"email":"user.email@signup.com","password":"111-222"}' http://localhost:3000/register

curl 'http://localhost:3000/register' -H 'Referer: http://localhost:3000/' -H 'Content-Type: application/json' -H 'Origin: http://localhost:3000' -H 'Connection: keep-alive' --data-raw '{"email":"test@test.com","password":"123456","name":"Test"}'
```


[localhost:3000/signin](http://localhost:3000/signin)
``` 
curl -X POST -d '{"email":"user.email@signup.com","password":"111-222"}' http://localhost:3000/signin

curl 'http://localhost:3000/signin' -H 'Referer: http://localhost:3000/' -H 'Content-Type: application/json' -H 'Origin: http://localhost:3000' -H 'Connection: keep-alive' --data-raw '{"email":"test@test.com","password":"123456"}'
```


-------------------


[origin](https://github.com/aneagoie/smart-brain-boost-api-dockerized)
