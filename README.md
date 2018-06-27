# Create-custom-fields-with-apex
~~~
String objectapiname = 'Content_Item__c';//replace with your object name
String fieldapiname = 'Country_Name';//replace with your field name
String fieldlabel = 'Country_Name';//replace with your field label
String fielddescription = 'Country Name';//replace with your field label

HttpRequest requestinside = new HttpRequest();
requestinside.setHeader('Authorization', 'Bearer ' + UserInfo.getSessionID());
requestinside.setHeader('Content-Type', 'application/json');
requestinside.setEndpoint(URL.getSalesforceBaseUrl().toExternalForm()+'/services/data/v41.0/tooling/sobjects/CustomField/');
requestinside.setMethod('POST');
String fieldDef = '{"Metadata" : ';
String metadef = '"type" : "Text","description" : "'+fielddescription+'", "inlineHelpText" : "","precision" : null,"label" : "'+fieldlabel+'","length" : 255,"required" : false'
fieldDef += '{'+metadef+'},';
fieldDef += '"FullName" : "'+objectapiname+'.'+fieldapiname+'__c"}';
system.debug(fieldDef);
requestinside.setBody(fieldDef);
HTTPResponse res = http.send(requestinside);
System.debug(res.getBody());
~~~~

## Multiple Fields Creation:

Put this code snippet in for loop and make a call for each field as below:
~~~
for(){
  String objectapiname = 'Content_Item__c';//replace with your object name
  String fieldapiname = 'Country_Name';//replace with your field name
  String fieldlabel = 'Country_Name';//replace with your field label
  String fielddescription = 'Country Name';//replace with your field label

  HttpRequest requestinside = new HttpRequest();
  requestinside.setHeader('Authorization', 'Bearer ' + UserInfo.getSessionID());
  requestinside.setHeader('Content-Type', 'application/json');
  requestinside.setEndpoint(URL.getSalesforceBaseUrl().toExternalForm()+'/services/data/v41.0/tooling/sobjects/CustomField/');
  requestinside.setMethod('POST');
  String fieldDef = '{"Metadata" : ';
  String metadef = '"type" : "Text","description" : "'+fielddescription+'", "inlineHelpText" : "","precision" : null,"label" : "'+fieldlabel+'","length" : 255,"required" : false'
  fieldDef += '{'+metadef+'},';
  fieldDef += '"FullName" : "'+objectapiname+'.'+fieldapiname+'__c"}';
  system.debug(fieldDef);
  requestinside.setBody(fieldDef);
  HTTPResponse res = http.send(requestinside);
  System.debug(res.getBody());

}
~~~
