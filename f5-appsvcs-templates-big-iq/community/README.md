BIG-IQ AS3 Templates submitted by the Community
===============================================

List of AS3 Templates 
---------------------

Templates (schemaOverlay) | Version | Description | Min AS3 version | Min BIG-IQ version
------------------------- | ------- | ----------- | --------------- | ------------------
| AS3-HTTPS-offload-lb-LTM-policy-ASM-splunk-template-big-iq | v2 | For load balancing an HTTPS application on port 443 with SSL offloading on BIG-IP using existing Certificate and Key on BIG-IP, custom TCP monitor and LTM Policy with a WAF policy sending its logs to Splunk. | 3.18 | 7.1
| AS3-F5-HTTP-lb-page-load-time-template-big-iq | v1 | For load balancing an HTTP application on port 80 with Page Load Time HTTP analytics and CSPM enabled (Client side Perf Monitoring javascript injection) [more details on K13849](https://support.f5.com/csp/article/K13849). | 3.12 | 7.0
| AS3-F5-TCP-lb-built-in-profile-template-big-iq | v1 | For load balancing a TCP-based application using one of the built-in TCP profile. | 3.18 | 7.1
| AS3-F5-HTTP-lb-TCP-analytics-key-template-big-iq | v1 | For load balancing an HTTP application on port 80 withTCP analytics using a user-provided key set in an iRule. | 3.18 | 7.1
| AS3-F5-DNS-FQDN-A-type-default-monitors-template-big-iq | v1 | For global load balancing distribution of DNS name resolution requests A type using default monitors. | 3.18 | 7.1

Importing AS3 templates to your BIG-IQ using a script
-----------------------------------------------------

1. Open an SSH session to your BIG-IQ, and log in as an admin.

2. From the command prompt, run the following sequence of commands. (You can copy and paste the entire sequence directly to the command line.)

**Note:** Replace ``*.json`` in the ``for`` loop with the name of the template you want to import if you don't want to import all the community templates present in the json folder.

```
bash
cd /home/admin;
rm -rf f5-big-iq*.tar.gz f5devcentral-f5-big-iq-*;
curl -L https://github.com/f5devcentral/f5-big-iq/tarball/7.1.0 > f5-big-iq.tar.gz;
tar -xzvf f5-big-iq.tar.gz;
cd f5devcentral-f5-big-iq-*/f5-appsvcs-templates-big-iq/community/json/;

for json in *.json; do 
curl -s -k -H "Content-Type: application/json" -X POST -d @$json http://localhost:8100/cm/global/appsvcs-templates ;
done
```
3. Log in to your primary BIG-IQ device and navigate to **Applications > APPLICATION TEMPLATES** and verify that the templates you imported are listed under **AS3 Templates**.

**Note:** Before you can use an AS3 template, it must be Published (read-only).

4. For more information on how to use an AS3 template to deploy an AS3 Application using the BIG-IQ, see [BIG-IQ documentation](https://support.f5.com/csp/knowledge-center/software/BIG-IQ?module=BIG-IQ%20Centralized%20Management&version=7.0.0)

Support
-------

Bugs and enhancements can be made by opening an issue within the GitHub repository.
