# Case 5: Ping Ya Later!
### Neython is an employee of the Internet Engineering Task Force (IETF) based out of the East Coast. Tired of the cold, he is looking to move to the West Coast and would like to network with management out there.
### Because of the time difference, he's worried about sending messages to people outside of their working hours. Because the IETF uses Webex, he's decided to build a script leveraging the Webex REST API and AWS serverless functions to send pre-written messages at a specific time automatically.

1. (**Free Response**) In a few sentences, describe what a serverless function is and why its a good choice for this small project.



2. (**Multiple Choice**) Neython first needs to determine how to access the Webex Teams API. Which of the following options is not a valid method for access?
   
    a. Third-party integration support via OAuth authentication, registered via the Webex developer dashboard.
    
    b. Personal access tokens retrieved from the Webex developer dashboard.
    
    c. Guest token via the JSON Web Token (JWT) standard, with guest issuers created via the Webex developer dashboard.
    
    d. Chatbot token via HTTP Basic authentication, registered via the Webex developer dashboard.


4. (**Drag and Drop**) To test the API, Neython begins by building a **curl** command to post a message to a specific room.

- Use the following code blocks to construct the command. *Note that not all blocks will be used and they must be ordered!*
    ```bash
    -H "{'roomId':'Y2klamsdflkm2k34m1oi1', 'text':'This is a test message'}" \
    ```
    ```bash
    curl --x POST \
    ```
    ```bash
    --url "https://webexapis.com/v1/messages" \
    ```
    ```bash
    -H "Authorization: Bearer YzFlZGExM2YtYjMdZi00YmVmLTk0MTMtZmE3NDc3Zkg5ODM3MGI4M2UxNTAtNGVh_PF84_1eb65fdf-9643-417f-9934-ad72cae0e11f" \
    ```
    ```bash
    -H "Content-Type":"application/json" \
    ```
    ```bash
    -H "Webex-API-Token: YzFlZGExM2YtYjMdZi00YmVmLTk0MTMtZmE3NDc3Zkg5ODM3MGI4M2UxNTAtNGVh_PF84_1eb65fdf-9643-417f-9934-ad72cae0e11f" \
    ```
    ```bash
    -d "{'roomId':'Y2klamsdflkm2k34m1oi1', 'text':'This is a test message'}" \
    ```
    ```bash
    curl --request POST \
    ```
    ```bash
    -u "https://webexapis.com/v1/messages" \
    ```


- After successful testing, Neython now wants to convert the **curl** command he just wrote to a Python script.
Use the below options to fill in the missing TODOs. *Note that not all options will be used.*

  
```python
""" Send Webex Message """ 

import TODO-1
import requests
import pprint 

URL = "https://webexapis.com/v1/messages"
PAYLOAD = { 
	TODO-2 : "Y2klamsdflkm2k34m1oi1" , 
	"text" : "This is a test message"
} 

HEADERS = {
	"Authorization": TODO-3, 
	"Content-Type": "application/json",
} 

RESPONSE = requests.request(TODO-4, URL, data=json.dumps(TODO-5), headers=HEADERS)

pprint.pprint(json.loads(RESPONSE.text))
```

| **OPTIONS** |  |
|--|--|
|Authentication  | Authorization |
|X-Cisco-Webex-API-Key| "YzFlZGExM2YtYjMdZi00YmVmLTk0MTMtZmE3NDc3Zkg5ODM3MGI4M2UxNTAtNGVh_PF84_1eb65fdf-9643-417f-9934-ad72cae0e11f"  |
|"roomId"| "room_id" |
|"POST"|"GET"|
|PAYLOAD|DATA|
|netmiko|json|

