BIG-IQ AS3 Template Library
===========================

**Note:** If you are looking for 7.0.0 AS3 Templates, select the [7.0.0](https://github.com/f5devcentral/f5-big-iq/tree/7.0.0) branch.

F5 maintains this BIG-IQ Application Services 3 Extension (AS3) template library to provide you with templates that you can either use directly or with just a few changes of your own. Use the instructions here to download these templates to your BIG-IQ system. Once downloaded, you can use these templates just as you would any other AS3 application template. AS3 templates perform on the BIG-IQ in much  the same way as they do on BIG-IP. For more detail on AS3 and how it works, refer to the CloudDocs content: [Using AS3 with BIG-IQ](https://clouddocs.f5.com/products/extensions/f5-appsvcs-extension/latest/userguide/big-iq.html). 

[Look for AS3 templates submitted by the community!](./f5-appsvcs-templates-big-iq/community)

List of AS3 F5 Default Templates 
--------------------------------

Templates (schemaOverlay) | Version | Description | Min AS3 version | Min BIG-IQ version
------------------------- | ------- | ----------- | --------------- | ------------------
| AS3-F5-HTTP-lb-template-big-iq-default | v1 | For load balancing an HTTP application on port 80 with HTTP analytics. | 3.12 | 7.0
| AS3-F5-HTTP-lb-traffic-capture-template-big-iq-default | v1 | For load balancing an HTTP application on port 80 with HTTP traffic capture and HTTP analytics. | 3.12 | 7.0
| AS3-F5-HTTPS-offload-lb-PEM-template-big-iq-default | v1 | For load balancing an HTTPS application on port 443 with SSL offloading on BIG-IP and using a custom HTTP monitor (Certificate and Key in PEM format) with HTTP analytics. | 3.12 | 7.0
| AS3-F5-HTTPS-offload-lb-existing-cert-template-big-iq-default | v1 | For load balancing an HTTPS application on port 443 with SSL offloading on BIG-IP using existing Certificate and Key on BIG-IP with HTTP analytics. | 3.12 | 7.0
| AS3-F5-HTTPS-offload-lb-existing-SSL-profile-template-big-iq-default |  v1 | For load balancing an HTTPS application on port 443 with SSL offloading on BIG-IP using existing SSL profile on BIG-IP. | 3.18 | 7.1
| AS3-F5-HTTPS-WAF-existing-lb-template-big-iq-default | v1 | For load balancing an HTTPS application on port 443 with a Web Application Firewall policy & certificates existing on BIG-IP and HTTP analytics. | 3.12 | 7.0
| AS3-F5-HTTPS-WAF-external-url-lb-template-big-iq-default | v2 | For load balancing an HTTPS application on port 443 with a Web Application Firewall (external URL) policy using an OWASP protection settings with minimum false positive (v13.1) and HTTP analytics. [Look for other ASM Policies Available on DevCentral](https://github.com/f5devcentral/f5-asm-policy-templates) | 3.18 | 7.1
| AS3-F5-TCP-lb-template-big-iq-default | v2 | For load balancing a TCP-based application with TCP analytics. | 3.18 | 7.1
| AS3-F5-FastL4-TCP-lb-template-big-iq-default | v2 | For load balancing a TCP-based application with a FastL4 profile and TCP analytics. | 3.18 | 7.1
| AS3-F5-UDP-lb-template-big-iq-default | v1 | For load balancing a UDP-based application. | 3.12 | 7.0
| AS3-F5-DNS-FQDN-A-type-template-big-iq-default | v1 | For global load balancing distribution of DNS name resolution requests A type. | 3.12 | 7.0
| AS3-F5-DCD-lb-ASM-request-logging-events-template-big-iq-default | v1 | For ASM request logging events load balancing to BIG-IQ DCDs. | 3.12 | 7.0

There are two methods you can use to download these templates and import then into your BIG-IQ so that you can use them. 

- If you are comfortable logging in to your BIG-IQ via SSH and executing a script, use **Importing AS3 templates to your BIG-IQ using a script**. This method uses an API call to access a JSON file.
- If you are more comfortable with an application with a graphical user interface, use **Importing AS3 templates to your BIG-IQ using Postman**. This method uses an application named Postman to import the templates directly to your BIG-IQ.

Importing AS3 templates to your BIG-IQ using a script
-----------------------------------------------------
The following steps assume that you have completed the initial setup for your BIG-IQ and have admin permissions to log in to it via SSH. Additionally, for the script to run successfully, the DNS lookup server addresses must be correctly specified. 

1. Open an SSH session to your BIG-IQ, and log in as an admin.

2. From the command prompt, run the following sequence of commands. (You can copy and paste the entire sequence directly to the command line.)

```
bash
cd /home/admin;
rm -rf f5-big-iq*.tar.gz f5devcentral-f5-big-iq-*;
curl -L https://github.com/f5devcentral/f5-big-iq/tarball/7.1.0 > f5-big-iq.tar.gz;
tar -xzvf f5-big-iq.tar.gz;
cd f5devcentral-f5-big-iq-*/f5-appsvcs-templates-big-iq/default/json/;

for json in *.json; do 
curl -s -k -H "Content-Type: application/json" -X POST -d @$json http://localhost:8100/cm/global/appsvcs-templates ;
done
```
3. Log in to your primary BIG-IQ device and navigate to **Applications > APPLICATION TEMPLATES** and verify that the templates you imported are listed under **AS3 Templates**.

![bigiq_as3_templates_ui](./images/bigiq_as3_templates_ui.png)

**Note:** Before you can use an AS3 template, it must be Published (read-only).

4. For more information on how to use an AS3 template to deploy an AS3 Application using the BIG-IQ, see [BIG-IQ documentation](https://support.f5.com/csp/knowledge-center/software/BIG-IQ?module=BIG-IQ%20Centralized%20Management&version=7.1.0)

Importing AS3 templates to your BIG-IQ using Postman
----------------------------------------------------

1. [Install the Postman application.](https://learning.getpostman.com/docs/postman/launching_postman/installation_and_updates/)

2. Use the Postman Import feature to import the Postman Collection and Environment. To do this:
   1. Click the **Import** button.
   1. Click **Import From Link**.
   1. For the Postman Collection, paste in the following: `https://raw.githubusercontent.com/f5devcentral/f5-big-iq/7.1.0/f5-appsvcs-templates-big-iq/default/postman/default-as3-f5-all-templates-big-iq.postman_collection.json` and then click **Import**.
   1. Repeat the last 3 sub-steps, but this time paste in the following for the Postman Environment:  `https://raw.githubusercontent.com/f5devcentral/f5-big-iq/7.1.0/f5-appsvcs-templates-big-iq/default/postman/default-as3-f5-all-templates-big-iq.postman_environment.json`.

![postman_collection_import](./images/postman_collection_import.png)

3. Set your `Primary BIG-IQ CM IP address` in the Postman Environment. To do this:
   1. Click the Settings icon to open the Manage Environments screen.
   1. Click `default-as3-f5-all-templates-big-iq`.
   1. For the `bigiq_mgmt` variable, type the management IP address of your BIG-IQ in the `CURRENT VALUE`
   1. Click **Update**.
   1. Close the Manage Environments screen.

![postman_collection_environment](./images/postman_collection_environment.png)

4. Specify the  BIG-IQ device's admin user `username` & `password`so that Postman can access it. To do this:
   1. Select the `POST` named `Authenticate to BIG-IQ`, as shown in the screen shot.
   1. On the Body tab, type:
   
   ```
   >"username": "admin",
   >"username": "admin",
   >"loginProviderName": "tmos",
   ```

   1. Save the collection.

![postman_collection_bigiq_auth](./images/postman_collection_bigiq_auth.png)

5. Run the Import Collection in this environment. To do this:
   1. Open the Postman Runner.
   1. For the Collection, select **default-as3-f5-all-templates-big-iq**.
   1. For the Environment, select **default-as3-f5-all-templates-big-iq**.
   1. Click **Run default-as3-f5-all-templates-big-iq**.

![postman_collection_runner](./images/postman_collection_runner.png)

6. When the Post Collection finishes, the result should be green status icons and  `200 OK` for each post.

![postman_collection_runner_passed](./images/postman_collection_runner_passed.png)

7. Log in to your primary BIG-IQ device and navigate to **Applications > APPLICATION TEMPLATES** and verify that the templates you imported are listed under **AS3 Templates**.

![bigiq_as3_templates_ui](./images/bigiq_as3_templates_ui.png)

**Note:** Before you can use an AS3 template, it must be Published (read-only).

8. For more information on how to use an AS3 template to deploy an AS3 Application using the BIG-IQ, see [BIG-IQ documentation](https://support.f5.com/csp/knowledge-center/software/BIG-IQ?module=BIG-IQ%20Centralized%20Management)

Support
-------

Bugs and enhancements can be made by opening an issue within the GitHub repository.

Because BIG-IQ is has been created and fully tested by F5 Networks, it is fully supported by F5. This means you can get assistance if necessary from [F5 Technical Support](https://www.f5.com/services/support).

## Copyright

Copyright 2014-2020 F5 Networks Inc.


### F5 Networks Contributor License Agreement

Before you start contributing to any project sponsored by F5 Networks, Inc. (F5) on GitHub, you will need to sign a Contributor License Agreement (CLA).  

If you are signing as an individual, we recommend that you talk to your employer (if applicable) before signing the CLA since some employment agreements may have restrictions on your contributions to other projects. Otherwise by submitting a CLA you represent that you are legally entitled to grant the licenses recited therein.  

If your employer has rights to intellectual property that you create, such as your contributions, you represent that you have received permission to make contributions on behalf of that employer, that your employer has waived such rights for your contributions, or that your employer has executed a separate CLA with F5.   

If you are signing on behalf of a company, you represent that you are legally entitled to grant the license recited therein. You represent further that each employee of the entity that submits contributions is authorized to submit such contributions on behalf of the entity pursuant to the CLA. 

