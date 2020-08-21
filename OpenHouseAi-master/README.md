# OpenHouse.AI Backend Test 

This is the application for OpenHouse.ai coding test.

## Installation
Please install [Python 3](python.org/downloads/) and add it to your terminal path.

After installing, run:
```bash
pip install -r requirements.txt
```

## To Run
In the project work directory run on the cmd:
```bash
python app.py 
```

Navigate to the default page [http://127.0.0.1:5000/](http://127.0.0.1:5000/)

## API End Points

### GET 

You can get requests in the following manner:

 To get all the user entities of the database. 
 
 [http://127.0.0.1:5000/user/all](http://127.0.0.1:5000/user/all)

 To get all the action entities of the database
 
 [http://127.0.0.1:5000/action/all](http://127.0.0.1:5000/action/all)

This endpoint retrieves all the action entities of the database. 

 To extract the whole logs or logs with specific params (/logs/userId=<userId>&logType=<logType>&lowerTimeRange=<lowerTimeRange>&upperTimeRange=<upperTimeRange>)

 [http://127.0.0.1:5000/logs](http://127.0.0.1:5000/logs)

### POST

 [http://127.0.0.1:5000/user](http://127.0.0.1:5000/api/v1/resources/user)

This endpoint is designed for the front end to dump the user id and sessionId into the database. It takes in two mandatory params:
- id - Mandatory. This is the user id 
- sessionId - Mandatory. This is the session id

 [http://127.0.0.1:5000/action](http://127.0.0.1:5000/api/v1/resources/action)

This endpoint is designed for the front end to dump the action logs into the database. It takes in five params but only one is mandatory (user_sessionId):
/action?user_sessionId=<user_sessionId>&type=<type>&viewedId=<viewedId>&locationX=<locationX>&locationY=<locationY>&pageTo=<pageTo>&pageFrom=<pageFrom>

## Test

The database is already uploaded in the github repository. If you would like to insert data please follow these steps:

1. To create the user entity using this post request with these id and sessionId params:
[http://127.0.0.1:5000/user?id=ABC123XYZ&sessionId=XYZ456ABC](http://127.0.0.1:5000/user?id=ABC123XYZ&sessionId=XYZ456ABC)

2. Next we will start adding the action entities using this post request with the specified params:

[http://127.0.0.1:5000/action?user_sessionId=XYZ456ABC&type=CLICK&locationX=52&locationY=11](http://127.0.0.1:5000/action?user_sessionId=XYZ456ABC&type=CLICK&locationX=52&locationY=11)

[http://127.0.0.1:5000/action?user_sessionId=XYZ456ABC&type=VIEW&viewedId=FDJKLHSLD](http://127.0.0.1:5000/action?user_sessionId=XYZ456ABC&type=VIEW&viewedId=FDJKLHSLD)

[http://127.0.0.1:5000/action?user_sessionId=XYZ456ABC&type=NAVIGATE&pageFrom=communities&pageTo=inventory](http://127.0.0.1:5000/action?user_sessionId=XYZ456ABC&type=NAVIGATE&pageFrom=communities&pageTo=inventory)


## To verify

You can use this get request to verify if data is added
 
 [http://127.0.0.1:5000/user/all](http://127.0.0.1:5000/user/all)

 [http://127.0.0.1:5000/action/all](http://127.0.0.1:5000/action/all)

 Lastly we can use this get request to retrieve all log files from the user id "ABC123XYZ": 
[http://127.0.0.1:5000/logs?userId=ABC123XYZ](http://127.0.0.1:5000/logdump?userId=ABC123XYZ)


## Follow Up Question


1. I would use a different database. As it usually handles large data I would look for cloud based database resources.

2. I would probably look at the characteristics of the scalable application in terms of performance, availability , reliability and manageability. I would try to enhance this app with libraries and APIs that are required for Saas operations.

3. I would create multiple hosts

4. As it takes multiple requests from the server I would use GraphQl rather using REST

