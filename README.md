[CyberSecurity NP](https://www.cybersecuritynp.org) is an organization dedicated to promoting the education of cyber security nationally in local communities. Check out our [Chapters](https://www.cybersecuritynp.org/chapters/)

![CyberSecurity NP](https://www.cybersecuritynp.org/wp-content/uploads/2019/07/logo-no-website.png)

======================================================================================
This a sample demo to demonstrate how we can automate the collection of threat intelligence and lauch an automated attack based on the collected intel.


* Prerequisites for making this demo work:

  * [Ruby](https://www.ruby-lang.org/en/documentation/installation/)
  * [Nexpose Runner](https://rubygems.org/gems/NexposeRunner/versions/0.0.5)

================================================================================

* How to Run *
scan --connection test.com [--exceptions_list_url raw.github.com/exceptions.txt] --username username1 --password password1 [--port 443] --site-name myfirstsite --ip-addresses 192.168.1.10 --scan-template full-audit [--engine_id 2] [--cleanup] [--no-gen-policy-report] [--no-gen-software-report] [--no-gen-xml-report] [--no-gen-audit-report]

