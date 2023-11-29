# Case 2: EZMoto
### EZMoto is new startup focused on making it easier to begin riding motorcycles. Principle Architect Karis is responsible for managing EZMoto's infrastructure. Because of their sudden growth, Karis is tasked with implementing automation workflows across their environment.
### EZMoto currently uses Catalyst Center to manage their enterprise equipment. To make inventory management easier, Karis wants to set up a script to retrieve all of their device information programmatically via Catalyst Center's REST API.

1. (**Drag and Drop**) Complete the following Python script to allow Karis to authenticate to their Catalyst Center instance. The username is *ezmoto-admin* with a password of *Motorcycle123!* and a Base64 encoding of *ZGV2bmV1dxNlcjpDaXNjbzEyMyA=*.

```python
import requests

base_url = "https://sandboxdnac.cisco.com"
auth_url = "/dna/system/api/v1/auth/token"

headers = {
	"Authorization": "Basic ZGV2bmV1dxNlcjpDaXNjbzEyMyA="
}

response = requests.request("POST", base_url+auth_url, headers=headers)

print(response.text)
```


- (**Multiple Choice**) Karis was successful in authenticating to the Catalyst Center instance and the API returned an authorization token. What HTTP status code is most likely to be in the response header?
  
  **a. 200** 
  
  b. 401
  
  c. 204
  
  d. 400

  The correct answer is A. The HTTP Status Code 200 OK will be returned after succesful authentication.
  Even though this is a POST request, because the API returns a token, 204 No Content is not the correct answer.


- (**Free Response**) It is often recommended to return an HTTP Status Code 404 when an unauthorized user attempts to query a private resource. In a few sentences,
describe the 404 response code and why developers recommend this.

Returning a HTTP Status Code 404 Not Found is best practice for protecting the visibiliy of private resources.
While an HTTP Status Code 401 Unauthorized might make sense since the user is unauthorized, returning a 401 reveals the existence of the resource, which should not be public knowledge.
Thus, returning a 404 ensures the user does not succesfully authenticate AND is not necessarily aware that the resource exists.

<br><br>

2. (**Multiple Choice**) What Catalyst Center API should Karis use to now retrieve the necessary device inventory information?
  
  **a. Intent API**
  
  b. Integration API
  
  c. Multivendor SDK
  
  d. Network API


The correct answer is A. The Intent API is a Northbound REST API that exposes specific capabilities of the Cisco DNA Center platform, including device inventory.

  
<br>

- (**Drag and Drop**) Complete the Python script to retrieve a list of network devices as JSON. 
```python
import requests
import json
import os

token = os.environ["AUTH_TOKEN"]
url = "https://sandboxdnac.cisco.com/dna/intent/api/v1/" + "network-devices"

headers = {
	"X-AUTH-TOKEN": token,
	"Accept": "application/json,
	"Content-Type": "application/json"
}

response = requests.request("GET", url, headers=headers)

print(response.text)
```


- (**Free Response**) In a few sentences, describe some differences between Catalyst Center's Intent API and Integration API. *Hint: What is an example use case for each API?*

The Intent API is a Northbound API meant to open up the capabilities of the DNA Center Platform. 
In contrast, the Integration API is a Westbound API which provides mechanisms 
for integrating Cisco DNA Assurance workflows and data with third-party IT Service Management (ITSM) solutions.
