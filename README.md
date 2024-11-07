import json
import requests

# Define the URL of the API
url = "https://www.example.com/api/v1/users"

# Get the user ID from the command line
user_id = input("Enter the user ID: ")

# Define the payload with the user ID
payload = {"user_id": user_id}

# Send a GET request to the API
response = requests.get(url, params=payload)

# Check if the request was successful
if response.status_code == 200:
    # Parse the response as JSON
    data = json.loads(response.text)
    
    # Print the user's information
    print(f"User ID: {data['user_id']}")
    print(f"First Name: {data['first_name']}")
    print(f"Last Name: {data['last_name']}")
    print(f"Email Address: {data['email']}")
else:
    # Print an error message
    print(f"Error: {response.status_code}")

