Introduction
============
This quickstart demonstrates the usage of a rules service which performs an age check.
The rules are specified using a DTABLE resource (and XLS resourceDetail) in the manifest.
The input is the incoming message content (an "Applicant").
The output is a boolean, and mapped using the implicit "globals" Map.

This quickstart also demonstrates how a domain property can be made available as a global variable inside your DRL.
See references to ${user.name} (system property) mapping to userName (domain property) mapping to userName (global variable) inside switchyard.xml.
Then look at Interview.drl and how the userName global variable is used in the DRL.

This quickstart can be executed using either a java interface or a web service interface.

![Rules Interview Quickstart](https://github.com/jboss-switchyard/quickstarts/raw/master/rules-interview-dtable/rules-interview-dtable.jpg)


Preqrequisites 
==============
Maven

Running the quickstart
======================


EAP
----------
1. Start EAP in standalone mode:

        ${AS}/bin/standalone.sh

2. Build and deploy the quickstart: 

        mvn install -Pdeploy

3. Submit a webservice request to invoke the SOAP gateway.  There are a number of ways to do this :
    - Submit a request with your preferred SOAP client - src/test/resources/xml contains 
      sample requests and the responses that you should see
    - Use the simple bundled SOAP client and the sample request XML e.g.
<br/>
```
        mvn exec:java
```
<br/>
    - SOAP-UI : Use the wsdl for this project (src/main/resources/wsdl/OrderService.wsdl) to 
      create a soap-ui project. Use the sample request (src/test/resources/xml/soap-request-pass.xml) 
      as an example of a sample request.  See the "Expected Output" section for the expected results. 


4. Undeploy the quickstart:

        mvn clean -Pdeploy


Wildfly
----------
1. Start Wildfly in standalone mode:

        ${AS}/bin/standalone.sh

2. Build and deploy the quickstart: 

        mvn install -Pdeploy

3. Submit a webservice request to invoke the SOAP gateway.  There are a number of ways to do this :
- Submit a request with your preferred SOAP client - src/test/resources/xml contains 
sample requests and the responses that you should see
- Use the simple bundled SOAP client and the sample request XML e.g.
<br/>
```
        mvn exec:java
```
<br/>
- SOAP-UI : Use the wsdl for this project (src/main/resources/wsdl/OrderService.wsdl) to 
create a soap-ui project. Use the sample request (src/test/resources/xml/soap-request-pass.xml) 
as an example of a sample request.  See the "Expected Output" section for the expected results. 


4. Undeploy the quickstart:

        mvn clean -Pdeploy


Karaf
----------
1. Start the Karaf server :

${KARAF_HOME}/bin/karaf

2. Add the features URL for the respective version of BXMS.   Replace {FUSE_BXMS_VERSION}
with the version of Fuse BXMS Integration that you are using (ex. 1.0.0): 

karaf@root> features:addurl mvn:org.jboss.integration.karaf/fuse-bxms-integration/${FUSE_BXMS_VERSION}/xml/features


3. Install the feature for the Rules Interview dtable quickstart :

karaf@root> features:install fuse-bxms-switchyard-quickstart-rules-interview-dtable

4. To submit a webservice request to invoke the SOAP gateway, run the quickstart client :
<br/>
```
mvn exec:java -Pkaraf
```
<br/>

5. Undeploy the quickstart:

karaf@root> features:uninstall fuse-bxms-switchyard-quickstart-rules-interview-dtable


Expected Output
===============
```
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
   <SOAP-ENV:Header/>
   <SOAP-ENV:Body>
      <urn:verifyResponse xmlns:urn="urn:switchyard-quickstart:rules-interview-dtable:0.1.0">
         <return>true</return>
      </urn:verifyResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```



## Further Reading

1. [Configuration Documentation](https://docs.jboss.org/author/display/SWITCHYARD/Configuration)
2. [Rules Service Documentation](https://docs.jboss.org/author/display/SWITCHYARD/Rules)
