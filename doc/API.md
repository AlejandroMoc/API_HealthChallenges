# Testing the API

To test the API, you can use Postman as follows.

## Users

### User Registration

To test user registration, enter the following data:

```
# Select POST and enter URL
http://localhost:3000/api/users/signup

# In Body, select Raw and paste the content.
{
    "name": "Pedro Equis",
    "email": "pedrox@sitio.com",
    "password": "PedroEquis654"
}
```

Press the "Send" button.
You should now see a success message as a response from Postman.

## User Deletion

To delete a user, you need the email and password.

```
# Select DELETE and enter URL.
http://localhost:3000/api/users/delete/

# In Body, select Raw as parameters. Paste the following content.

{
    "email": "pedrox@sitio.com",
    "password": "PedroEquis654"
}
```

Press the "Send" button.
You should now see a success message as a response from Postman.

### Querying a User's Challenges

To query a user's challenges, you need the user's ID.

```
# Select GET and enter the URL
http://localhost:3000/api/users/:userId/challenges

# For example, if the user ID is 688c21220143a333e8f61366
http://localhost:3000/api/users/688c21220143a333e8f61366/challenges
```

Press the "Send" button.
You should now see a success message as a response from Postman.

## Challenges

### Challenge Registration

- The challenge name and description are defined by "name" and "description".
- The duration of a challenge in days is defined by "numberDays".
- The challenge type, "goalType", must be "daily" or "accumulative".
- The number to be reached in the challenge is defined by "goalNumber".

```
# Select POST and enter URL
http://localhost:3000/api/challenges/create

# In Body, select Raw and paste the content
{
    "name": "Walk More",
    "description" : "Take 5000 steps daily for a week.",

    "type": "steps",
    "numberDays": 7,

    "goalType": "daily",
    "goalNumber": 5000
}
```

Press the "Send" button.
You should now see a success message as a response from Postman.

### Delete a Challenge

- ":id" represents the ID of the challenge to be deleted.

```
# Select DELETE and enter the URL. In Body, select None
http://localhost:3000/api/challenges/delete/:id

# For example, if the ID is 688c21220143a333e8f61366
http://localhost:3000/api/challenges/delete/688c21220143a333e8f61366
```

Press the "Send" button.
You should now see a success message as a response from Postman.

### Challenge Leaderboard

Retrieves the user ranking for a specific challenge, ordered by progress.

- ":challengeId" refers to the ID of the challenge

```
# Select GET and enter the URL
http://localhost:3000/api/challenges/:challengeId/leaderboard

# Example with ID 688c21220143a333e8f61366
http://localhost:3000/api/challenges/688c21220143a333e8f61366/leaderboard
```

Press the "Send" button.
You should now see a success message as a response from Postman.

## Activities

### Register an Activity for a User

- The "userId" is the ID of the user.
- The date recorded for the activity is represented by "date".
- "Value" and "type" represent the value and type of the activity being recorded.
- "Type" can only be "steps", "sleep", or "cardio_points".

```
# Select POST and enter URL
http://localhost:3000/api/activities/register

# In Body, select Raw and paste the content
{
    "userId": "USER_ID",
    "date": "2025-07-31",
    "type": "steps",
    "value": 7500
    
}
```
