Prerequisites:
1. For all request use Authentication:
Type: Basic Auth
Username: {Username_Auth}
Password: {Password_Auth}

TC_1: Verify "POST petstore_host/user" endpoint 

1.1 Open Postman and send request:
	POST {{petstore_host}}/user 
with body:
{
  "id": 00001,
  "username": "test_name_1",
  "firstName": "first_name_1",
  "lastName": "last_name_1",
  "email": "email_1@gmail.com",
  "password": "password_1",
  "phone": "+380660000001",
  "userStatus": 1
}
ER: 201 Created.

1.2 Go to {DB_name} DB > {env} > Collection {name} and find record with "username":"test_name_1".
ER: Recodr is presented with body:
{
  "id": 00001,
  "username": "test_name_1",
  "firstName": "first_name_1",
  "lastName": "last_name_1",
  "email": "email_1@gmail.com",
  "password": "password_1",
  "phone": "+380660000001",
  "userStatus": 1
}

1.3 Open Postman and send request:
	POST {{petstore_host}}/user 
with body:
{
  "id": 00001,
  "username": "test_name_2",
  "firstName": "first_name_2",
  "lastName": "last_name_2",
  "email": "email_2@gmail.com",
  "password": "password_2",
  "phone": "+380660000002",
  "userStatus": 1
}
ER: 40X error code.

1.4 Go to {DB_name} DB > {env} > Collection {name} and find record with "username":"test_name_2".
ER: Record is not presented.

1.5 Open Postman and send request:
	POST {{petstore_host}}/user 
with body:
{
  "id": 00002,
  "username": "test_name_1",
  "firstName": "first_name_2",
  "lastName": "last_name_2",
  "email": "email_2@gmail.com",
  "password": "password_2",
  "phone": "+380660000002",
  "userStatus": 1
}
ER: 40X error code.

1.6 Go to {DB_name} DB > {env} > Collection {name} and find record with "username":"test_name_1" and "id":00002.
ER: Record is not presented.

1.7 Open Postman and send request:
	POST {{petstore_host}}/user 
with body:
{
  "id": 00003,
  "username": "test_name_3",
  "firstName": "first_name_3",
  "lastName": "last_name_3",
  "email": "email_1@gmail.com",
  "password": "password_3",
  "phone": "+380660000003",
  "userStatus": 1
}
ER: 40X error code
1.8 Go to {DB_name} DB > {env} > Collection {name} and find record with "username":"test_name_3" and "id":00003.
ER: Record is not presented.

1.9 Open Postman and send request:
	POST {{petstore_host}}/user 
with body:
{
  "id": 00004,
  "username": "test_name_4",
  "firstName": "first_name_4",
  "lastName": "last_name_4",
  "email": "email_4@gmail.com",
  "password": "password_4",
  "phone": "+380660000001",
  "userStatus": 1
}
ER: 40X error code

1.10 Go to {DB_name} DB > {env} > Collection {name} and find record with "username":"test_name_4" and "id":00004.
ER: Record is not presented.


TC_2: Verify "GET petstore_host/user/{username}" endpoint 

2.1 Open Postman and send request:
	GET {{petstore_host}}/user/{username}
 "username": "test_name_1"
ER: 200 and in body responce is presented: 
{
  "id": 00001,
  "username": "test_name_2",
  "firstName": "first_name_2",
  "lastName": "last_name_2",
  "email": "email_2@gmail.com",
  "password": "password_2",
  "phone": "+380660000002",
  "userStatus": 1
}

2.2 Open Postman and send request:
	GET {{petstore_host}}/user/{username}
 "username": "test_name_999"
ER: 404 User not found

2.3 Open Postman and send request:
	GET {{petstore_host}}/user/{username}
 "username": "."
ER: 400 Invalid username supplied.
