The Import-Packages ordering in the jar file MANIFEST file needs modified and should be the following

Import-Package:
    javax.xml.bind.annotation,
    javax.ws.rs;version="[2.0,3)",
    javax.ws.rs.core;version="[2.0,3)",
    org.apache.commons.httpclient;version="[3.1,4)",
    org.apache.commons.httpclient.methods;version="[3.1,4)",
    org.osgi.service.blueprint;version="[1.0.0,2.0.0)",
    com.wordnik.swagger.jaxrs.config,
    com.wordnik.swagger.jaxrs.listing,
    com.wordnik.swagger.annotations,
    com.fasterxml.jackson.core;version="[2.1,3)",
    com.fasterxml.jackson.databind;version="[2.1,3)",
    com.fasterxml.jackson.annotation;version="[2.1,3)",
    javax.ws.rs.ext;version="[2.0,3)",
    javax.xml.bind,
    javax.wsdl,
    com.fasterxml.jackson.jaxrs.json;version="[2.0,3)"

I dont know why the ordering causes problems when deploying in servicemix. Still looking into this.


To run a web client:
--------------------
Open a browser and go to the following URL:

   http://localhost:8181/cxf/crm/customerservice/customers/123

It should display an XML representation for customer 123.

Changing /cxf servlet alias
---------------------------
By default CXF Servlet is assigned a '/cxf' alias. You can
change it in a couple of ways

a. Add org.apache.cxf.osgi.cfg to the /etc directory and set the
   'org.apache.cxf.servlet.context' property, for example:
   
   org.apache.cxf.servlet.context=/custom

b. Use shell config commands, for example:

     config:edit org.apache.cxf.osgi   
     config:propset org.apache.cxf.servlet.context /super
     config:update
