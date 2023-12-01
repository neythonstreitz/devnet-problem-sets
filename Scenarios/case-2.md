# Case 2: EZMoto
### EZMoto is new startup focused on making it easier to begin riding motorcycles. Principle Architect Karis is responsible for managing EZMoto's infrastructure. Because of their sudden growth, Karis is tasked with implementing automation workflows across their environment.
### EZMoto currently uses Catalyst Center to manage their enterprise equipment. To make inventory management easier, Karis wants to set up a script to retrieve all of their device information programmatically via Catalyst Center's REST API.

1. (**Drag and Drop**) Complete the following Python script to allow Karis to authenticate to their Catalyst Center instance. The username is *ezmoto-admin* with a password of *Motorcycle123!* and a Base64 encoding of *ZGV2bmV1dxNlcjpDaXNjbzEyMyA=*.

```python
import TODO-1

base_url = "https://sandboxdnac.cisco.com"
auth_url = TODO-2

headers = {
	"Authorization": TODO-3
}

response = requests.request(TODO-4, TODO-5, headers=headers)

print(response.text)
```
|**OPTIONS**  |  |
|--|--|
| request | requests |
|"/dna/system/api/v1/auth/token"|"/catalyst/api/v1/auth"|
|"/dna/api/v1/authenticate"|"Basic ZGV2bmV1dxNlcjpDaXNjbzEyMyA="|
|{"username":"ezmoto-admin", "password":"Motorcycle123!"}|"POST" |
|"Basic ezmoto-admin:Motorcycle123!"|"GET"|
|auth_url|base_url+auth_url|

<br><br>

- (**Multiple Choice**) Karis was successful in authenticating to the Catalyst Center instance and the API returned an authorization token. What HTTP status code is most likely to be in the response header?
  
  a. 200 
  
  b. 401
  
  c. 204
  
  d. 400

<br><br>

- (**Free Response**) It is often recommended to return an HTTP Status Code 404 when an unauthorized user attempts to query a private resource. In a few sentences,
describe the 404 response code and why developers recommend this.


<br><br>

2. (**Multiple Choice**) What Catalyst Center API should Karis use to now retrieve the necessary device inventory information?
  
	  a. Intent API
	  
	  b. Integration API
	  
	  c. Multivendor SDK
	  
	  d. Network API
  
<br><br>

- (**Drag and Drop**) Complete the Python script to retrieve a list of network devices as JSON. 
```python
import requests
import json
import TODO-1

token = os.environ["AUTH_TOKEN"]
url = "https://sandboxdnac.cisco.com/dna/intent/api/v1/" + TODO-2

headers = {
	TODO-3: token,
	"Accept": TODO-4,
	"Content-Type": "application/json"
}

response = requests.request(TODO-5, url, headers=headers)

print(response.text)
```
|**OPTIONS**  |  |
|--|--|
| ncclient | os |
|"network-devices"|"organization/network/devices"|
|"Cisco-API-Token"|"X-AUTH-TOKEN"|
|"Authentication"|"POST"|
|"application/xml"|"application/json"|
|"devices/get-devices"|"GET"|

<br><br>

- (**Free Response**) In a few sentences, describe some differences between Catalyst Center's Intent API and Integration API. *Hint: What is an example use case for each API?*

<br><br>

