String toolingSOQL = '/services/data/v36.0/tooling/query?q=Select+DeveloperName+From+CustomObject';
String baseURL = URL.getSalesforceBaseUrl().toExternalForm();
String endpoint = baseUrl+toolingSOQL;


Http newReq = new Http();
HttpRequest hreq = new HttpRequest();
hreq.setHeader('Authorization', 'Bearer' + UserInfo.getSessionId());
hreq.setTimeout(60000);
hreq.setEndpoint(endpoint);
hreq.setMethod('GET');
HttpResponse hresp = newReq.send(hreq);


String body = hresp.getBody();
System.debug('ResponseBody: '+ body);



------------------------------------------------------------------------
    
String toolingSOQL = '/services/data/v36.0/tooling/query?q=Select+DeveloperName+From+CustomObject';
String baseURL = URL.getSalesforceBaseUrl().toExternalForm();
String endpoint = baseUrl+toolingSOQL;


HttpRequest req = new HttpRequest();
req.setHeader('Authorization', 'Bearer ' + UserInfo.getSessionID());
req.setHeader('Content-Type', 'application/json');
//req.setEndpoint(endpoint);
req.setEndpoint('https://rushisatpute422-dev-ed.develop.lightning.force.com/services/data/v36.0/tooling/apexManifest');
req.setMethod('GET');

Http h = new Http();
HttpResponse res = h.send(req);
String str = res.getBody();
//system.debug(str);

//Map<String, Object> obj1 = (Map<String, Object>)JSON.deserializeUntyped(str);
//List<Object> a = (List<Object>)obj1.get('name');
List<Object> a = (List<Object>)JSON.deserializeUntyped(str);
for(Integer i =0; i < a.size(); i++)
{
    Map<String, Object> obj1 = (Map<String, Object>)a[i];
	String className = (String)obj1.get('name');
	System.debug('Apex Class Name: '+ className);
}

String sessionId = UserInfo.getOrganizationId()+''+UserInfo.getSessionId().SubString(15);
System.debug('Session ID:'+ sessionId);


List<Schema.SObjectType> gd = Schema.getGlobalDescribe().Values();
for(Integer i=0; i< gd.size(); i++)
{
    System.debug('Object Name: '+ gd[i]);
}

List<String> str = new List<String>();

for ( Schema.SObjectType o : Schema.getGlobalDescribe().values() )
		{
            Schema.DescribeSObjectResult objResult = o.getDescribe();
            //system.debug( 'Sobject: ' + objResult );
            //system.debug( 'Sobject API Name: ' + objResult.getName() );
            str.add(objResult.getName());
        }

for(String s : str)
{
    System.debug('Object Name:'+ s);
}

DemoMap.getJsonResults();

String objectAPIName = 'Case' ; //any object api
  Schema.DescribeSObjectResult sobjectResult = Schema.getGlobalDescribe().get(objectAPIName).getDescribe();
   List<Schema.RecordTypeInfo> recordTypeInfo = sobjectResult.getRecordTypeInfos();
    Map<String,Id> mapofCaseRecordTypeNameandId = new Map<String,Id>();
    for(Schema.RecordTypeInfo info : recordTypeInfo){
     mapofCaseRecordTypeNameandId.put(info.getName(),info.getRecordTypeId());
    }
   system.debug('***mapofCaseRecordTypeNameandId*'+mapofCaseRecordTypeNameandId);




Order_Event__e orderEvt = new Order_Event__e(OrderName__c='Rushikesh31234');

Database.SaveResult sr = EventBus.publish(orderEvt);
if(sr.isSuccess())
{
    System.debug('Success!' + sr.getId());
}
else
{
    System.debug('Error: ' + sr.getErrors());
}
>>>>>>>>>>>>>>>>>>>>>>>>>>
  Publish a Event for Testing Purpose
>>>>>>>>>>>>>>>>>>>>>>>>>>
    
Test__e TestEvt = new Test__e();
TestEvt.PhoneNumber__c = 957961070.0;
Database.SaveResult sr = EventBus.publish(TestEvt);
if(sr.isSuccess())
{
    System.debug('Success!' + sr.getId());
}
else
{
    System.debug('Error: ' + sr.getErrors());
}



>>>>>>>>>>>>>>>>
    
    
    Http http = new Http();
HttpRequest request = new HttpRequest();
request.setEndpoint('https://putsreq.com/V2TNujCj4lfJ1aTPcy4O');
request.setMethod('GET');
HttpResponse response = http.send(request);
// If the request is successful, parse the JSON response.
if(response.getStatusCode() == 200) {
    // Deserialize the JSON string into collections of primitive data types.
    System.debug(response.getBody());
   
}



Event e = new Event();
//e.Email='rushisatpute422@gmail.com';
e.DurationInMinutes = 1;
e.ActivityDateTime = System.today();// 04/26/2023;
insert e;

System.debug(System.today());


HttpRequest req = new HttpRequest();
req.setEndpoint('callout:My_Named_Credential/services');
req.setMethod('GET');
Http http = new Http();
HTTPResponse res = http.send(req);
System.debug(res.getBody());

----------------------------------------//New Code------------------------------

Http http = new Http();
HttpRequest request = new HttpRequest();
request.setEndpoint('callout:Named_Cred_Example/queryAll/?q=Select+ Id+,Name +From+ Account+ LIMIT+ 10');
request.setMethod('GET');

HttpResponse response = http.send(request);

if(response.getStatusCode() == 200) {
    // Deserialize the JSON string

    Map<String, Object> results = (Map<String, Object>) JSON.deserializeUntyped(response.getBody());

    List<Object> lstObj = (List<Object>) results.get('ELEMENT_NAME');
    System.debug('Received the following ELEMENT_NAME:');

    for(Object obj: lstObj) {
        System.debug(obj);
    }
}



>>>>>>>>>>>>>>>>>>>>>
    
    
    
    .
Integer i =  Integer.ValueOf(10.0);
System.debug('Value Of Integer: '+ i);
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
    
    
    
List<EmailMessage> emailMsgListt = new List<EmailMessage>();
EmailMessage e = new EmailMessage();
e.id='02s5i00000AnSmCAAV';
emailMsgListt.add(e);
List<Attachment> attachLis = new List<Attachment>();
CreateCaseWithAttachment.createNewCaseWithAttachment(emailMsgListt);




Http http = new Http();
HttpRequest request = new HttpRequest();
request.setEndpoint('https://th-apex-http-callout.herokuapp.com/animals');
request.setMethod('GET');
HttpResponse response = http.send(request);
// If the request is successful, parse the JSON response.
if(response.getStatusCode() == 200) {
    // Deserialize the JSON string into collections of primitive data types.
    Map<String, Object> results = (Map<String, Object>) JSON.deserializeUntyped(response.getBody());
    // Cast the values in the 'animals' key as a list
    List<Object> animals = (List<Object>) results.get('animals');
    System.debug('Received the following animals:');
    for(Object animal: animals) {
        System.debug(animal);
    }
}


List<QuickTextUsage> recordsToDelete = [SELECT Id FROM QuickTextUsage];
delete recordsToDelete;





List<Order__c> OrderList = [Select Id,TestDate__c from Order__c where Account__c='0015i00000jZoKsAAK'];
List<AggregateResult> newOrderList= [Select MAX(TestDate__c) maxDateTime from Order__c where Id IN :OrderList];
Date updatedDate;
for (AggregateResult ar : newOrderList)
{
	updatedDate = Date.Valueof(ar.get('maxDateTime'));
}
System.debug('Order Max Date: '+ updatedDate);

List<Order__c> OrderList = [Select Id, TestDate__c from Order__c];
List<Order__c> AccountIds = [Select Account__c from Order__c where Id IN :OrderList];
System.debug('Accounts : '+ AccountIds[0].Account__c);

System.debug('Order List: ' + [SELECT TestDate__c FROM Order__c ORDER BY TestDate__c ASC LIMIT 1]);




Set<String> str = new Set<String>();
str.add('RSS');
str.add('kkk');

for(String s: str)
{
    System.debug('String s: '+ s);
}
String accid = '0015i00000jZoKsAAK';
Date MinOrderDate = [Select TestDate__c from Order__c where Account__c =: accid ORDER BY TestDate__c ASC LIMIT 1][0].TestDate__c;
System.debug('Minimum Date: '+ MinOrderDate);


 List<Id> contentDocumentIds = new List<Id>();
        for (ContentVersion contentVersion : [SELECT ContentDocumentId FROM ContentVersion]) {
            contentDocumentIds.add(contentVersion.ContentDocumentId);
        }

        // Delete ContentDocuments
        if (!contentDocumentIds.isEmpty()) {
            delete [SELECT Id FROM ContentDocument WHERE Id IN :contentDocumentIds];
        }


List<String> bigObjectNames = new List<String>();

// Retrieve all custom big objects
for (Schema.SObjectType objectType : Schema.getGlobalDescribe().values()) {
    if (objectType.getDescribe().isCustom() && objectType.getDescribe().isBigObject()) {
        bigObjectNames.add(objectType.getDescribe().getName());
    }
}

// Now bigObjectNames list contains the API names of all custom big objects
System.debug(bigObjectNames);


EmailMessage Emsg = [SELECT Id FROM EmailMessage LIMIT 1][0];




testBigObj__b obj1 = new testBigObj__b();
    obj1.Subject__c = 'Test';
	obj1.Id__c = 124324;
Database.SaveResult sr = Database.insertimmediate(obj1);

if (sr.isSuccess()) 
{ System.debug('Successfully inserted Big Obj: ' + sr.getId()); 
}
else { for(Database.Error err : sr.getErrors()) 
{ System.debug('The following error has occurred.'); 
System.debug(err.getStatusCode() + ': ' + err.getMessage());
 System.debug('Big Obj that affected this error: ' + err.getFields()); 
}
     }


Account a = new Account(Name='Test Acc anonymous window');
System.debug('Account Name: '+ a.Name);
