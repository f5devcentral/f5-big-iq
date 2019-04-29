BIG-IQ Templates
================

**Note:** These templates are supported only with BIG-IQ 7.0.0 and above.

Use this API to define an [Application Services 3 Extension (AS3)](https://clouddocs.f5.com/products/extensions/f5-appsvcs-extension/latest/) template on BIG-IQ. You can use AS3 on BIG-IQ in largely the same way as on BIG-IP. This is described in the AS3 documentation: [Using AS3 with BIG-IQ](https://clouddocs.f5.com/products/extensions/f5-appsvcs-extension/latest/userguide/big-iq.html). With BIG-IQ, declarations use an AS3 template which is defined in BIG-IQ. For an example of an AS3 declaration that uses an AS3 template, see the AS3 documentation: [Using declarations with AS3 templates](https://clouddocs.f5.com/products/extensions/f5-appsvcs-extension/latest/userguide/big-iq.html#template). You can use the [AS3 Declare API](https://clouddocs.f5networks.net/products/big-iq/mgmt-api/v7.0.0/ApiReferences/bigiq_public_api_ref/r_as3_declare.html) to post the AS3 declaration to BIG-IP and you can use the [AS3 Deploy API](https://clouddocs.f5networks.net/products/big-iq/mgmt-api/v7.0.0/ApiReferences/bigiq_public_api_ref/r_as3_deploy.html) from BIG-IQ to deploy an application.

You can find a list of default AS3 templates in this repository in 2 different forms:

* Postman Collection (see below instructions)
* JSON file (see the [BIG-IQ API documentation](https://clouddocs.f5.com/products/big-iq/mgmt-api/latest/ApiReferences/bigiq_public_api_ref/r_as3_template.html) for details related to creating AS3 templates)

Instructions on how to import AS3 templates using Postman
---------------------------------------------------------

1. [Install the Postman app](https://learning.getpostman.com/docs/postman/launching_postman/installation_and_updates/)

2. Import the two Postman collections available on this github repository under `f5-appsvcs-templates > default > postman`

![postman_collection_import](./images/postman_collection_import.png)

3. Set your `Primary BIG-IQ CM IP address` in the Postman Environment.

![postman_collection_environment](./images/postman_collection_environment.png)

4. Set your BIG-IQ admin user `username` & `password` in the `POST` called `Authenticate to BIG-IQ`

![postman_collection_bigiq_auth](./images/postman_collection_bigiq_auth.png)

5. Open the Postman runner, select the Collection and Environment called `default-as3-f5-all-templates` and click `Run default-a3-f5...`

![postman_collection_runner](./images/postman_collection_runner.png)

6. The result of the Postman running should be `200 OK`

![postman_collection_runner_passed](./images/postman_collection_runner_passed.png)

7. Log in to your `Primary BIG-IQ CM` and navigate to the `Applications` tab > `APPLICATION TEMPLATES` > `AS3 Templates` and verify they are all showing correctly.

![bigiq_as3_templates_ui](./images/bigiq_as3_templates_ui.png)

**Note:** In order to use the templates, you will need to publish them first.

8. For more information on how to use the template to deploy an AS3 Application using the BIG-IQ, see [BIG-IQ documentation](https://support.f5.com/csp/knowledge-center/software/BIG-IQ?module=BIG-IQ%20Centralized%20Management&version=7.0.0)

Support
-------

Bugs and enhancements can be made by opening an issue within the GitHub repository.
