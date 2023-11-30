# Case 3: Olive
### Leah and Sophia are the founders of a new Mediterranean restaurant, *Olive*. After a successful first year, they plan on expanding their business to multiple new locations.
### Since their team is quite small, they've decided to leverage the Meraki SDK to create new networks programmatically.

---
1. (**Free Response**) In a few sentences, describe the benefits of using an SDK to interact with an API.

A software development kit (SDK) is a set of tools that developers can use to create software/applications for a specific platform. 
Typically those tools include a set of libraries, APIs, documentation, sample code, and processes that make it easier for developers to work with the platform.
Some advantages of using an SDK include:
- Faster and more efficient development since developers don't need to write code from scratch.
- Better troubleshooting and support with documentation, community resources, and analyics features.
- For the platform, increased security and brand control since anyone building integrations with the SDK will be using the same building blocks developed and controlled by the company.


---
2.  (**Multiple Choice**) Leah and Sophia first need to authenticate to their Meraki environment. Where should they go to retrieve their authentication token.

    a. They can create one using Base64 encoding with a username and password.
    
    b. They can enable the API and generate a token via the Meraki dashboard.
    
    c. The Meraki SDK does not require authentication.
    
    d. They can generate a JSON Security Token by submitting authentication credentials in the body of an HTTP request.

The correct answer is B. To start using the Meraki API, you must enable the API within the Meraki dashboard and retrieve an API token to be used in any requests.
The API key is specified within the request header like so:
```python
header = {"X-Cisco-Meraki-API-Key": API_TOKEN}
```

---
3. Leah and Sophia begin testing the API via a **curl** command. Use the following image to answer the questions.

  	![image](https://github.com/neythonstreitz/devnet-problem-sets/assets/144170135/33445c97-5bdc-45b9-86e9-cd73777d8983)

- (**Multiple Choice**) Which of the following statements are true of their attempt? (Choose two)

    a. The request was successful and returned a list of organizations as JSON in the body.
    
    b. The request was not successful due to an issue with the headers.
    
    c. The use of the -I flag returns the HTTP response headers and removing it would output the response body instead.
    
    d. The response returns the content in XML.


The correct answer is B, C. Notice that the curl request returned an HTTP status code of ```HTTP/2 401```. The HTTP Status Code 401 Unauthorized indicates that the 
request could not be completed because it lacks valid authentication credentials. Why did the request fail? 
A typo in the authentication key! The correct value is ```X-Cisco-Meraki-API-Key```, but the request used ```X-Meraki-API-Key```.

Furthermore, the reason the **curl** command returned the response headers is due to the -I flag being used. Removing the -I flag only returns the response body:

<img width="569" alt="Screenshot 2023-11-30 at 10 47 43 AM" src="https://github.com/neythonstreitz/devnet-problem-sets/assets/144170135/2524f346-4464-4cac-acca-8066d1a89674">

We can now see that the response body indicates an error with the API key, just as we thought.

---
4. (**Drag and Drop**) Order the following code blocks to complete Leah and Sophia's *create-new-network* Python script. 
*All blocks will be used.*


```python
from meraki_sdk.meraki_sdk_client import MerakiSdkClient

X_CISCO_MERAKI_API_KEY = "15dadafskjlhawe234rgknKJhdfd34vm3"

MERAKI = MerakiSdkClient(X_CISCO_MERAKI_API_KEY)

ORGS = MERAKI.organizations.get_organizations()
for ORG in ORGS:
	print("Org ID: {} and Org Name: {}".format(ORG['id'], ORG['name']))

organization_id =  ORGS[0]['id']
name =  'RTP Restaurant' 
product_types =  ['appliance', 'switch', 'wireless'] 

response = dashboard.organizations.createOrganizationNetwork(
	organization_id, name, product_types, 
	tags=['tag1',  'tag2'], 
	timeZone='America/Los_Angeles', 
	copyFromNetworkId='N_24329156', 
	notes='New RTP location network')
```

The correct order is shown above. In general, it is best practice to indicate the imported libraries at the top of the script.
Next, static variables are defined including the API key.
We then use the API key to create a connection with the Meraki Dashboard API, which allows us to run requests without having to continously authenticate.


After retrieving the organizations in the Meraki environment, we retrieve the ID, name, and product types to query in our final call.
Finally, we create a new network called 'RTP Restaurant' within our selected organization, indicated by the ID.
