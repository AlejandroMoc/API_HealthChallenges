# Testing the API

To test the API, you can use `curl` from your terminal. Make sure the API is running (`npm run dev`) before running these commands.

## Users

### User Registration

To test user registration, send a POST request with the following data:

```bash
curl -X POST http://localhost:3000/api/users/signup \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Pedro Equis",
    "email": "pedrox@sitio.com",
    "password": "PedroEquis654"
  }'
```

You should now see a success message as a response.

## User Deletion

To delete a user, you need the email and password:

```bash
curl -X DELETE http://localhost:3000/api/users/delete/ \
  -H "Content-Type: application/json" \
  -d '{
    "email": "pedrox@sitio.com",
    "password": "PedroEquis654"
  }'
```

You should now see a success message as a response.

### Querying a User's Challenges

To query a user's challenges, you need the user's ID:

```bash
# For example, if the user ID is 688c21220143a333e8f61366
curl http://localhost:3000/api/users/688c21220143a333e8f61366/challenges
```

You should now see a success message as a response.

## Challenges

### Challenge Registration

- The challenge name and description are defined by "name" and "description".
- The duration of a challenge in days is defined by "numberDays".
- The challenge type, "goalType", must be "daily" or "accumulative".
- The number to be reached in the challenge is defined by "goalNumber".

```bash
curl -X POST http://localhost:3000/api/challenges/create \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Walk More",
    "description": "Take 5000 steps daily for a week.",
    "type": "steps",
    "numberDays": 7,
    "goalType": "daily",
    "goalNumber": 5000
  }'
```

You should now see a success message as a response.

### Delete a Challenge

- ":id" represents the ID of the challenge to be deleted.

```bash
# For example, if the ID is 688c21220143a333e8f61366
curl -X DELETE http://localhost:3000/api/challenges/delete/688c21220143a333e8f61366
```

You should now see a success message as a response.

### Challenge Leaderboard

Retrieves the user ranking for a specific challenge, ordered by progress.

- ":challengeId" refers to the ID of the challenge

```bash
# Example with ID 688c21220143a333e8f61366
curl http://localhost:3000/api/challenges/688c21220143a333e8f61366/leaderboard
```

You should now see a success message as a response.

## Activities

### Register an Activity for a User

- The "userId" is the ID of the user.
- The date recorded for the activity is represented by "date".
- "Value" and "type" represent the value and type of the activity being recorded.
- "Type" can only be "steps", "sleep", or "cardio_points".

```bash
curl -X POST http://localhost:3000/api/activities/register \
  -H "Content-Type: application/json" \
  -d '{
    "userId": "USER_ID",
    "date": "2025-07-31",
    "type": "steps",
    "value": 7500
  }'
```

You should now see a success message as a response.