BIG-IQ AS3 Templates
================

**Note:** These templates are supported only with BIG-IQ 7.0.0 and above.

F5 maintains this BIG-IQ Application Services 3 Extension (AS3) template library to provide you with templates that you can either use directly or with just a few changes of your own. Use the instructions here to download these templates to your BIG-IQ system. Once downloaded, you can use these templates just as you would any other AS3 application template. AS3 templates perform on the BIG-IQ in uch  the same way as they do on BIG-IP. For more detail on how AS3 and how it works, refer to the CloudDocs content: [Using AS3 with BIG-IQ](https://clouddocs.f5.com/products/extensions/f5-appsvcs-extension/latest/userguide/big-iq.html). 

The AS3 templates in this repository are available in 2 formats:

* A Postman Collection & Environment. Instructions for downloading and importing these templates to your BIG-IQ user interface are provided below.
* A JSON file. Instructions for using this JSON file and API calls to use AS3 templates are provided in our CloudDocs content: BIG-IQ API documentation](https://clouddocs.f5.com/products/big-iq/mgmt-api/latest/ApiReferences/bigiq_public_api_ref/r_as3_template.html).

Importing AS3 templates to your BIG-IQ using Postman
---------------------------------------------------------

1. [Install the Postman application.](https://learning.getpostman.com/docs/postman/launching_postman/installation_and_updates/)

2. Use the Postman Import feature to import the Postman Collection and Environment. To do this:
   1. Click the **Import** button.
   1. Click **Import From Link**.
   1. Paste in the following for the Postman Collection: `https://raw.githubusercontent.com/f5devcentral/f5-big-iq/7.0.0/f5-appsvcs-templates/default/postman/default-as3-f5-all-templates.postman_collection.json` and then click **Import**.
   1. Repeast the last 3 sub-steps, but this type paste in the following for the Postman Environment:  `https://raw.githubusercontent.com/f5devcentral/f5-big-iq/7.0.0/f5-appsvcs-templates/default/postman/default-as3-f5-all-templates.postman_environment.json`.

![postman_collection_import](./images/postman_collection_import.png)

3. Set your `Primary BIG-IQ CM IP address` in the Postman Environment. To do this:
   1. Click the Settings icon to open the Manage Environments screen.
   1. Click `default-as3-f5-all-templates`.
   1. For the `bigiq_mgmt` variable, type the management IP address of your BIG-IQ.
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

![postman_collection_bigiq_auth](./images/postman_collection_bigiq_auth.png)

5. Run the Import Collection in this environment. To do this:
   1. Open the Postman Runner.
   1. For the Collection, select **default-as3-f5-all-templates**.
   1. For the Environment, select **default-as3-f5-all-templates**.
   1. Click **Run default-as3-f5-all-templates**.

![postman_collection_runner](./images/postman_collection_runner.png)

6. When the Post Collection finishes, the result should be green status icons and  `200 OK` for each post.

![postman_collection_runner_passed](./images/postman_collection_runner_passed.png)

7. Log in to your primary BIG-IQ device and navigate to **Applications > APPLICATION TEMPLATES > AS3 Templates** and verify that the AS3 templates you imported are listed.

![bigiq_as3_templates_ui](./images/bigiq_as3_templates_ui.png)

**Note:** Before you can use a AS3 template, it must be Published (read-only).

8. For more information on how to use the AS3 template to deploy an AS3 Application using the BIG-IQ, see [BIG-IQ documentation](https://support.f5.com/csp/knowledge-center/software/BIG-IQ?module=BIG-IQ%20Centralized%20Management&version=7.0.0)

Support
-------

Bugs and enhancements can be made by opening an issue within the GitHub repository.
