# Cynerio backend assignment

### Description
The server enables our team members to checkin/checkout on tasks they are working on and thus we
can understand the efforts we invest in every task

### Assumptions
 - Users can't checkin to a task when a previous task is already in checkin status by them.
 - There is no task name validation, so any task can be worked on by any user multiple times.
 - report will return only completed tasks that were checked-out.
 - mySQL DB was used for persistence. 

### Running
1. Download & install "MySQL Community Server" from https://dev.mysql.com/downloads/
2. add ".env" file for local sql configuration:
```
# node app environment variables
PORT=3000

# database connection environment variables
DB_HOST=localhost
DB_USER=
DB_NAME=
DB_PASSWORD=
```

3. To start and run the server, execute this command in your root directory:
```
npm run start
```
4. to run tests execute this command in your root directory:
```
npm run test
```

### API
 - `/checkin` - Mark that work on a specific assignment has begun
 - `/checkout/:user` - Mark that current active assignment is no longer being worked on
 - `/report` - Get report of all users and time invested in each task


### Response
 - return 400 for any logic errors:
   - "POST checkin failed - invalid input"
   - "POST checkin failed - user did not checkout"
   - "POST checkout failed - user did not checkin"

 - return 500 for server errors
 - return 200 for success

### Examples
- checkin
```
curl --location --request POST 'http://localhost:3000/checkin' \
--header 'Content-Type: application/json' \
--data-raw '{
    "user": "Bob",
    "task": "Sample assignment 1"
}'
```

- checkout
```
curl --location --request POST 'http://localhost:3000/checkout/bob' \
--data-raw ''
```

- report
```
curl --location --request GET 'http://localhost:3000/report'
```
