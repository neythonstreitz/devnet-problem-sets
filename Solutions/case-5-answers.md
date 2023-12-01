# Case 5: Ping Ya Later!
### Neython is an employee of the Internet Engineering Task Force (IETF) based out of the East Coast. Tired of the cold, he is looking to move to the West Coast and would like to network with management out there.
### Because of the time difference, he's worried about sending messages to people outside of their working hours. Because the IETF uses Webex, he's decided to build a script leveraging the Webex REST API and AWS Lambda serverless functions to send pre-written messages at a specific time automatically.

1. (**Free Response**) In a few sentences, describe what serverless computing is and why its a good choice for this small project.

  **Answer:**
  <br>
  Serverless computing allows users to write and develop code without worrying about the underlying infrastructure.
  This removes the need to reserve and pay for a fixed amount of servers, since the service is auto-scaling.
  In this example, Neython is unlikely to require constant posting of messages and will only need functions to execute at specific times.
  As a result, using AWS Lambdas will allow him to execute functions on an as-needed basis, and rapidly scale down to zero when not in use.
  This has the potential to save him time, cost, and resources developing his solution.


---
2. (**Multiple Choice**) Neython first needs to determine how to access the Webex Teams API. Which of the following options is not a valid method for access?
   
    a. Third-party integration support via OAuth authentication, registered via the Webex developer dashboard.
    
    b. Personal access tokens retrieved from the Webex developer dashboard.
    
    c. Guest token via the JSON Web Token (JWT) standard, with guest issuers created via the Webex developer dashboard.
    
    d. Chatbot token via HTTP Basic authentication, registered via the Webex developer dashboard.

  **Answer:**
  The correct answer is D. Chatbots do not use HTTP Basic authentication.
  Developers can create a bot directly in the Webex developer dashboard and receive a token to be used for authentication.
  Then, developers can authenticate using Bearer authentication by passing the token in the header of their request.


---
4. (**Drag and Drop**) To test the API, Neython begins by building a **curl** command to post a message to a specific room.

- Use the following code blocks to construct the command. *Note that not all blocks will be used and they must be ordered!*
    ```bash
    curl --request POST \
    -H "Authorization: Bearer YzFlZGExM2YtYjMdZi00YmVmLTk0MTMtZmE3NDc3Zkg5ODM3MGI4M2UxNTAtNGVh_PF84_1eb65fdf-9643-417f-9934-ad72cae0e11f" \
    -H "Content-Type":"application/json" \
    -d "{'roomId':'Y2klamsdflkm2k34m1oi1', 'text':'This is a test message'}" \
    --url "https://webexapis.com/v1/messages" \
    ```

- After successful testing, Neython now wants to convert the **curl** command he just wrote to a Python script.
Use the below options to fill in the missing TODOs. *Note that not all options will be used.*

  
```python
""" Send Webex Message """ 

import json
import requests
import pprint 

URL = "https://webexapis.com/v1/messages"
PAYLOAD = { 
	"roomId" : "Y2klamsdflkm2k34m1oi1" , 
	"text" : "This is a test message"
} 

HEADERS = {
	"Authorization": "YzFlZGExM2YtYjMdZi00YmVmLTk0MTMtZmE3NDc3Zkg5ODM3MGI4M2UxNTAtNGVh_PF84_1eb65fdf-9643-417f-9934-ad72cae0e11f", 
	"Content-Type": "application/json",
} 

RESPONSE = requests.request("POST", URL, data=json.dumps(PAYLOAD), headers=HEADERS)

pprint.pprint(json.loads(RESPONSE.text))
```
