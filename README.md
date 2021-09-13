First you need a system account. This takes 10 working days. You'll receive part of it via email and will need to call the DeX Helpdesk to get the rest of it.

https://dex.dss.gov.au/dex-user-access-request-form

Install suds:
``` pip3 install pip3 install zeep```

This code should get you a listing of endpoints. Then print out some information about your organisation:
```python
#!/usr/bin/python3
from zeep import Client
from zeep.wsse.username import UsernameToken

client = Client('https://api.dss.gov.au/datacollection/dex?wsdl',
                wsse=UsernameToken('<USERNAME>', '<PASSWORD>'))

print(dir(client.service))

result = client.service.GetOrganisation()
print(result.body)
```

Output:
```
Forcing soap:address location to HTTPS
['AddCase', 'AddClient', 'AddOutlet', 'AddSession', 'DeleteCase', 'DeleteClient', 'DeleteOutlet', 'DeleteSession', 'GetAssessmentReferenceDetails', 'GetCase',
'GetClient', 'GetOrganisation', 'GetOrganisationActivities', 'GetOutlet', 'GetOutletActivities', 'GetReferenceData', 'GetSession', 'GetUser', 'Ping',
'SearchCase', 'SearchClient', 'UpdateCase', 'UpdateClient', 'UpdateClientAssessments', 'UpdateOutlet', 'UpdateSession', 'UpdateSessionAssessments',
'ValidateForDuplicateClient', '__class__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__get__', '__getattribute__', '__gt__',
'__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__self__', '__self_class__',
'__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__thisclass__']
{
    'TransactionStatus': {
        'TransactionStatusCode': 'Success',
        'Messages': None
    },
    'Organisation': {
        'Name':

...

```

Stay tuned...
