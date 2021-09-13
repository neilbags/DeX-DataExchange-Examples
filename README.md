First you need a system account. This takes 10 working days. You'll receive part of it via email and will need to call the DeX Helpdesk to get the rest of it.

https://dex.dss.gov.au/dex-user-access-request-form

I was first trying to use suds, and was able to authenticate however I kept getting 400 errors and never figured out why.

Install zeep:
``` pip3 install pip3 install zeep```

This code should get you a listing of endpoints. Then print out some information about your user account and organisation:
```python
#!/usr/bin/python3
from zeep import Client, Settings
from zeep.wsse.username import UsernameToken

settings = Settings(strict=False, raw_response=False, xml_huge_tree=True)
client = Client('https://api.dss.gov.au/datacollection/dex?wsdl',
                wsse=UsernameToken('<USERNAME>', '<PASSWORD>'), settings=settings)
result = client.service.GetUser()
print(dir(client.service))
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
    'User': {
        'UserName': 
        
...

```

If you need to see the raw XML, set `raw_response=True` and look at `result.content`.


Stay tuned...
