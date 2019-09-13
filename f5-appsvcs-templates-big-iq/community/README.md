BIG-IQ AS3 Community Templates
==============================

Browse through Community templates below submited by users.


Importing AS3 templates to your BIG-IQ using a script
-----------------------------------------------------

1. Open an SSH session to your BIG-IQ, and log in as an admin.

2. From the command prompt, run the following sequence of commands. (You can copy and paste the entire sequence directly to the command line.)

```
bash
cd /home/admin;
rm -rf f5-big-iq*.tar.gz f5devcentral-f5-big-iq-*;
curl -L https://github.com/f5devcentral/f5-big-iq/tarball/7.0.0 > f5-big-iq.tar.gz;
tar -xzvf f5-big-iq.tar.gz;
cd f5devcentral-f5-big-iq-*/f5-appsvcs-templates-big-iq/community/json/;

for json in *.json; do 
curl -s -k -H "Content-Type: application/json" -X POST -d @$json http://localhost:8100/cm/global/appsvcs-templates ;
done
```
3. Log in to your primary BIG-IQ device and navigate to **Applications > APPLICATION TEMPLATES** and verify that the templates you imported are listed under **AS3 Templates**.

![bigiq_as3_templates_ui](./images/bigiq_as3_templates_ui.png)

**Note:** Before you can use an AS3 template, it must be Published (read-only).

4. For more information on how to use an AS3 template to deploy an AS3 Application using the BIG-IQ, see [BIG-IQ documentation](https://support.f5.com/csp/knowledge-center/software/BIG-IQ?module=BIG-IQ%20Centralized%20Management&version=7.0.0)

Support
-------

Bugs and enhancements can be made by opening an issue within the GitHub repository.
