# Face detection API - Server (Dockerized) with [Client](https://github.com/tom2kota/face-detection-client)


```
npm i

npm audit fix

npm start
```

```
sudo docker-compose up
sudo docker-compose up --build

sudo docker-compose ps
sudo docker-compose down

sudo docker ps
sudo docker stop
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
backend               | [nodemon] 2.0.4
backend               | [nodemon] to restart at any time, enter `rs`
backend               | [nodemon] watching path(s): *.*
backend               | [nodemon] watching extensions: js,mjs,json
backend               | [nodemon] starting `node server.js`
backend               | ........... Face Detection Server App ...........  
backend               |             is running on port: {3001}

```

---------------


## endpoints & curl


[localhost:3001](http://localhost:3001/)


[localhost:3001/register](http://localhost:3001/register)


```
curl -X POST 'http://localhost:3001/register' -H 'User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0' -H 'Accept: */*' -H 'Accept-Language: ru-RU,ru;q=0.8,en-US;q=0.5,en;q=0.3' --compressed -H 'Referer: http://localhost:3000/' -H 'Content-Type: application/json' -H 'Origin: http://localhost:3000' -H 'Connection: keep-alive' --data-raw '{"email":"user1.email@signup.com","password":"1234","name":"User"}'
```

```
curl -X POST 'http://localhost:3001/register' -H 'User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0' -H 'Accept: */*' -H 'Accept-Language: ru-RU,ru;q=0.8,en-US;q=0.5,en;q=0.3' --compressed -H 'Referer: http://localhost:3000/' -H 'Content-Type: application/json' -H 'Origin: http://localhost:3000' -H 'Connection: keep-alive' -d '{"email":"user2.email@signup.com","password":"1234","name":"User"}'
```


``` 
curl -X POST 'http://localhost:3001/register' -H 'Accept: */*' --compressed -H 'Referer: http://localhost:3000/' -H 'Content-Type: application/json' -H 'Origin: http://localhost:3000' -H 'Connection: keep-alive' -d '{"email":"user3.email@signup.com","password":"1234","name":"User"}'
```


``` 
curl -X POST 'http://localhost:3001/register' -H 'Accept: */*' -H 'Content-Type: application/json'  -d '{"email":"user4.email@signup.com","password":"1234","name":"User"}'
```


--------


[localhost:3001/signin](http://localhost:3001/signin)

``` 
curl -X POST 'http://localhost:3001/signin' -H 'Accept: */*' -H 'Content-Type: application/json'  -d '{"email":"user4.email@signup.com","password":"1234"}'
```


```
curl 'http://localhost:3001/signin' -H 'User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0' -H 'Accept: */*' -H 'Accept-Language: ru-RU,ru;q=0.8,en-US;q=0.5,en;q=0.3' --compressed -H 'Referer: http://localhost:3000/' -H 'Content-Type: application/json' -H 'Origin: http://localhost:3000' -H 'Connection: keep-alive' --data-raw '{"email":"user4.email@signup.com","password":"1234"}'
```


---------

[localhost:3001/imageurl](http://localhost:3001/imageurl)
```
curl 'http://localhost:3001/imageurl' -H 'User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0' -H 'Accept: */*' -H 'Accept-Language: ru-RU,ru;q=0.8,en-US;q=0.5,en;q=0.3' --compressed -H 'Referer: http://localhost:3000/' -H 'Content-Type: application/json' -H 'Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6InVzZXI0LmVtYWlsQHNpZ251cC5jb20iLCJpYXQiOjE1OTQzMjY4ODQsImV4cCI6MTU5NDQ5OTY4NH0.KCFPmbGqNA1ac2lHJKwz62igZhZwTiEjOEeTuHmgcGA' -H 'Origin: http://localhost:3000' -H 'Connection: keep-alive' --data-raw '{"input":"https://static01.nyt.com/images/2019/10/02/video/02-still-for-america-room-loop/02-still-for-america-room-loop-jumbo.jpg"}'
```

```
curl 'http://localhost:3001/imageurl' -H 'Content-Type: application/json' -H 'Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6InVzZXI0LmVtYWlsQHNpZ251cC5jb20iLCJpYXQiOjE1OTQzMjY4ODQsImV4cCI6MTU5NDQ5OTY4NH0.KCFPmbGqNA1ac2lHJKwz62igZhZwTiEjOEeTuHmgcGA' -d '{"input":"https://static01.nyt.com/images/2019/10/02/video/02-still-for-america-room-loop/02-still-for-america-room-loop-jumbo.jpg"}'
```


----------

[localhost:3001/profile/1](http://localhost:3001/profile/1)

```
curl 'http://localhost:3001/profile/1' -H 'Content-Type: application/json' -H 'Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6InVzZXI0LmVtYWlsQHNpZ251cC5jb20iLCJpYXQiOjE1OTQzMjc1MzcsImV4cCI6MTU5NDUwMDMzN30.4T_ufvUd5v8dJDdv8hin0fGezy75rrkbc0XuIU8pzAo' -H 'Origin: http://localhost:3000' -H 'Connection: keep-alive' --data-raw '{"formInput":{"name":"New Name","age":"11","pet":"cat"}}'
```

-------------------


[origin](https://github.com/aneagoie/smart-brain-boost-api-dockerized)