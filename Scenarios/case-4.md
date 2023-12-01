# Case 4: DIPPOMODE
### Sebastian is developing a new Meraki Marketplace integration called DIPPOMODE. It provides shoplifting and theft detection by leveraging custom computer vision models on Meraki's MV lines of cameras.
### By cross-referencing video footage of the checkout lines with customers exiting the store, DIPPOMODE can alert businesses of customers accidentally or deliberately not scanning items at checkout.

1. Sebastian beings by creating a Python script that queries all cameras on a 1 second time interval via REST API calls.
   His approach passes all tests when using 2 cameras, however he knows that the customers he is marketing his integration towards will have many more cameras.

- (**FREE RESPONSE**) In a few sentences, describe the potential drawbacks of his approach when scaling the integration to large customer environments.

<br><br>

- (**Multiple Choice**) What HTTP status code is Sebastian most likely to see when testing the script on an environment with 50 cameras?
  *Remember, his script will attempt to query 50 cameras EVERY second.*
  
    a. 404
    
    b. 200
    
    c. 201
    
    d. 429

<br><br>

- (**Multiple Choice**) Which of the following new approaches does NOT address the issues with his initial attempt?

    a. Streaming data via the MV Camera's built-in MQTT support.
    
    b. Switching to a webhook based approach.
    
    c. Using the Dashboard APIs action batch support to perform multiple requests in a single transaction.
    
    d. Using the Dashboard APIs pagination support to ensure only a limited, specific amount of information is returned per request.

<br><br>

2. Sebastian is using Github to track his integration's source code. In the future, Sebastian hopes to hire a team of developers to work together on the integration.
- (**Drag and Drop**) Order the following pseudo-code commands to represent Sebastian's most likely workflow while developing his application.

    ```bash
    git commit ...
    ```
    ```bash
    git add ...
    ```
    ```bash
    git pull ...
    ```
    ```bash
    git push ...
    ```

<br><br>

3. To further enhance his integration, Sebastian is offering Infrastructure as Code (IaC) features via Ansible, to allow businesses to easily deploy their cameras. Below is a sample Ansible playbook he's developed.
```yaml
- name:  Update all
  cisco.meraki.devices_camera_sense:
    meraki_api_key: "{{meraki_api_key}}"
    meraki_base_url: "{{meraki_base_url}}"
    meraki_single_request_timeout: "{{meraki_single_request_timeout}}"
    meraki_certificate_path: "{{meraki_certificate_path}}"
    meraki_requests_proxy: "{{meraki_requests_proxy}}"
    meraki_wait_on_rate_limit: "{{meraki_wait_on_rate_limit}}"
    meraki_nginx_429_retry_wait_time: "{{meraki_nginx_429_retry_wait_time}}"
    meraki_action_batch_retry_wait_time: "{{meraki_action_batch_retry_wait_time}}"
    meraki_retry_4xx_error: "{{meraki_retry_4xx_error}}"
    meraki_retry_4xx_error_wait_time: "{{meraki_retry_4xx_error_wait_time}}"
    meraki_maximum_retries: "{{meraki_maximum_retries}}"
    meraki_output_log: "{{meraki_output_log}}"
    meraki_log_file_prefix: "{{meraki_log_file_prefix}}"
    meraki_log_path: "{{meraki_log_path}}"
    meraki_print_console: "{{meraki_print_console}}"
    meraki_suppress_logging: "{{meraki_suppress_logging}}"
    meraki_simulate: "{{meraki_simulate}}"
    meraki_be_geo_id: "{{meraki_be_geo_id}}"
    meraki_use_iterator_for_get_pages: "{{meraki_use_iterator_for_get_pages}}"
    meraki_inherit_logging_config: "{{meraki_inherit_logging_config}}"
    state: present
    audioDetection:
      enabled: false
    mqttBrokerId: '1234'
    senseEnabled: true
    serial: 'kjhf387h13jj'
```

- (**Multiple Choice**) Which of the following statements is true of the above playbook? (Choose three)
  
	a. The playbook is leveraging the devices_camera_sense module from the cisco.meraki collection.

	b. If an MV camera fails to configure its MV Sense settings, the playbook will continue to apply changes to all other cameras.

	c. If MV sense is installed, the playbook will ensure that the package is updated to the latest version.

	d. The playbook ensures all MV Cameras in the environment have MV Sense enabled, and its settings synchronized.

	e. The playbook updates the meraki_api_key and meraki_base_url across all the MV Cameras in the environment.

	f. MQTT data streaming is enabled across all cameras.

<br><br>
