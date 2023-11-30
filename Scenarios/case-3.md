# Case 3: Olive
### Leah and Sophia are the founders of a new Mediterranean restaurant, *Olive*. After a successful first year, they plan on expanding their business to multiple new locations.
### Since their team is quite small, they've decided to leverage the Meraki SDK to create new networks programmatically.

1. (**Free Response**) In a few sentences, describe the benefits of using an SDK to interact with an API.
<br><br>

2.  (**Multiple Choice**) Leah and Sophia first need to authenticate to their Meraki environment. Where should they go to retrieve their authentication token.

    a. They can create one using Base64 encoding with a username and password.
    
    b. They can enable the API and generate a token via the Meraki dashboard.
    
    c. The Meraki SDK does not require authentication.
    
    d. They can generate a JSON Security Token by submitting authentication credentials in the body of an HTTP request.

<br>

3. Leah and Sophia begin testing the API via a **curl** command. Use the following image to answer the questions.

  	![image](https://github.com/neythonstreitz/devnet-problem-sets/assets/144170135/33445c97-5bdc-45b9-86e9-cd73777d8983)

- (**Multiple Choice**) Which of the following statements are true of their attempt? (Choose two)

    a. The request was successful and returned a list of organizations as JSON in the body.
    
    b. The request was not successful due to an issue with the headers.
    
    c. The use of the -I flag returns the HTTP response headers and removing it would output the response body instead.
    
    d. The response returns the content in XML.


4. (**Drag and Drop**) Order the following code blocks to complete Leah and Sophia's *create-new-network* Python script. 
*All blocks will be used.*


```python
response = dashboard.organizations.createOrganizationNetwork(
	organization_id, name, product_types, 
	tags=['tag1',  'tag2'], 
	timeZone='America/Los_Angeles', 
	copyFromNetworkId='N_24329156', 
	notes='New RTP location network')
```
```python
organization_id =  ORGS[0]['id']
name =  'RTP Restaurant' 
product_types =  ['appliance', 'switch', 'wireless'] 
```
```python
ORGS = MERAKI.organizations.get_organizations()
for ORG in ORGS:
	print("Org ID: {} and Org Name: {}".format(ORG['id'], ORG['name']))
```

```python
from meraki_sdk.meraki_sdk_client import MerakiSdkClient

X_CISCO_MERAKI_API_KEY = "15dadafskjlhawe234rgknKJhdfd34vm3"

MERAKI = MerakiSdkClient(X_CISCO_MERAKI_API_KEY)
```
