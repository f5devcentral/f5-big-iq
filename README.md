BIG-IQ Templates
================

**Note:** These templates are supported only with BIG-IQ 7.0.0 and above.

Use this API to define an [Application Services 3 Extension (AS3)](https://clouddocs.f5.com/products/extensions/f5-appsvcs-extension/latest/) template on BIG-IQ. You can use AS3 on BIG-IQ in largely the same way as on BIG-IP and described in the AS3 documentation: [Using AS3 with BIG-IQ](https://clouddocs.f5.com/products/extensions/f5-appsvcs-extension/latest/userguide/big-iq.html). With BIG-IQ, declarations use an AS3 template which is defined in BIG-IQ. For an example of an AS3 declaration that uses an AS3 template, see the AS3 documentation: [Using declarations with AS3 templates](https://clouddocs.f5.com/products/extensions/f5-appsvcs-extension/latest/userguide/big-iq.html#template). You can use the [AS3 Declare API](https://clouddocs.f5networks.net/products/big-iq/mgmt-api/v7.0.0/ApiReferences/bigiq_public_api_ref/r_as3_declare.html) to post the AS3 declaration to BIG-IP and you can use the [AS3 Deploy API](https://clouddocs.f5networks.net/products/big-iq/mgmt-api/v7.0.0/ApiReferences/bigiq_public_api_ref/r_as3_deploy.html) from BIG-IQ to deploy an application.

You can find a list of default AS3 templates in this repository in 2 different forms:

* A Postman collection. Instructions for using these in the BIG-IQ user interface are provided below.
* A JSON file. The [BIG-IQ API documentation](https://clouddocs.f5.com/products/big-iq/mgmt-api/latest/ApiReferences/bigiq_public_api_ref/r_as3_template.html) provides instruction for using API calls to use AS3 templates.

Instructions on how to import AS3 templates using Postman
---------------------------------------------------------

1. [Install the Postman application.](https://learning.getpostman.com/docs/postman/launching_postman/installation_and_updates/)

2. Use the Postman Import feature to import the Postman collections available on this github repository under `f5-appsvcs-templates > default > postman`

![postman_collection_import](./images/postman_collection_import.png)

3. Set your `Primary BIG-IQ CM IP address` in the Postman environment. To do this, you set the value of the `bigiq_mgmt` variable to the management IP address of your BIG-IQ.

![postman_collection_environment](./images/postman_collection_environment.png)

4. Specify the  BIG-IQ device's admin user `username` & `password`so that Postman can access it. To do this, edit the `POST` named `Authenticate to BIG-IQ`, as shown in the screen shot.

![postman_collection_bigiq_auth](./images/postman_collection_bigiq_auth.png)

5. Open the Postman runner, select the Collection and Environement called `default-as3-f5-all-templates` and click `Run default-a3-f5...`

![postman_collection_runner](./images/postman_collection_runner.png)

6. The result of the Postman running should be `200 OK`

![postman_collection_runner_passed](./images/postman_collection_runner_passed.png)

7. Login to your `Primary BIG-IQ CM` and navigate to the `Applications` tab > `APPLICATION TEMPLATES` > `AS3 Templates` and verify that the AS3 templates you imported are listed.

![bigiq_as3_templates_ui](./images/bigiq_as3_templates_ui.png)

**Note:** Before you can a template, it must be Published (read-only).

8. For more information on how to use the template to deploy AS3 Application using the BIG-IQ, see [BIG-IQ documentation](https://support.f5.com/csp/knowledge-center/software/BIG-IQ?module=BIG-IQ%20Centralized%20Management&version=7.0.0)

Support
-------

Bugs and enhancements can be made by opening an issue within the GitHub repository.
