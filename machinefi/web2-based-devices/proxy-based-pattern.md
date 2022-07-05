# Proxy-based Pattern

In order to integrate the W3bStream framework with existing Web2-based IoT businesses, the proxy-based integration pattern is employed. \
\
This integration approach simplifies the integration process and requires only minimal changes on the backend of a Web2-based IoT system. \
\
While such an integration is able to accommodate a wide range of conventional Web2-based IoT businesses and minimize the digital transformation risks, all the IoT data is still collected by third parties and users do not truly own the data.

![](<../../.gitbook/assets/Screen Shot 2022-06-20 at 1.38.17 PM.png>)

As previously seen throughout this documentation, the proxy-based integration pattern essentially uses a Web2-based IoT system as a trusted data source. The client application sends data collected from the Web2-based application to the W3bStream node(s) which then interacts with the blockchain and triggers a smart contract for executing token related operations.&#x20;
