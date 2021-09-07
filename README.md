First you need a system account. This takes 10 working days. You'll receive part of it via email and will need to call the DeX Helpdesk to get the rest of it.

https://dex.dss.gov.au/dex-user-access-request-form

Install suds:
``` pip3 install suds-community```

This code should get you a listing of endpoints. Make sure you get your credentials right because you are locked-out after 5 attempts.
```python
#!/usr/bin/python3
from suds.client import Client
from suds.wsse import *
import logging

logging.basicConfig(level=logging.INFO)
logging.getLogger('suds.client').setLevel(logging.DEBUG)

url = 'https://api.dss.gov.au/datacollection/dex?wsdl'
client = Client(url)
security = Security()
token = UsernameToken('YOUR-USERNAME', 'YOUR-PASSWORD')
security.tokens.append(token)
client.set_options(wsse=security)
print(client)
```

Output:
```
Suds ( https://fedorahosted.org/suds/ )  version: 0.8.5

Service ( DEXService ) tns="http://api.socialservices.gov.au/DataCollection/DEX"
   Prefixes (14)
      ns0 = "http://api.socialservices.gov.au/Common"
      ns1 = "http://api.socialservices.gov.au/DataCollection/Assessment"
      ns2 = "http://api.socialservices.gov.au/DataCollection/Case"
      ns3 = "http://api.socialservices.gov.au/DataCollection/Common"
      ns4 = "http://api.socialservices.gov.au/DataCollection/Extensions"
      ns5 = "http://api.socialservices.gov.au/DataCollection/Organisation"
      ns6 = "http://api.socialservices.gov.au/DataCollection/Recipient"
      ns7 = "http://api.socialservices.gov.au/ebo/Address"
      ns8 = "http://api.socialservices.gov.au/ebo/DataCollection/Assessment"
      ns9 = "http://api.socialservices.gov.au/ebo/DataCollection/Case"
      ns10 = "http://api.socialservices.gov.au/ebo/DataCollection/Organisation"
      ns11 = "http://api.socialservices.gov.au/ebo/DataCollection/Recipient"
      ns12 = "http://api.socialservices.gov.au/ebo/DataCollection/Reference"
      ns13 = "http://api.socialservices.gov.au/ebo/DataCollection/Session"
   Ports (1):
      (DEX)
         Methods (28):
            AddCase(ns9:CaseDetailEditable Case, ns4:ArrayOfCaseClient Clients)
            AddClient(ns11:ClientBusinessDataExtended Client, xs:boolean HasValidatedForDuplicateClient)
            AddOutlet(ns10:OutletDetailsExtended OutletDetails)
            AddSession(xs:string CaseId, ns4:SessionDetailsExtended Session)
            DeleteCase(xs:string CaseId)
            DeleteClient(xs:string ClientId)
            DeleteOutlet(xs:int OutletId)
            DeleteSession(xs:string CaseId, xs:string SessionId)
            GetAssessmentReferenceDetails(xs:string ScoreTypeCode)
            GetCase(xs:string CaseId)
            GetClient(xs:string ClientId)
            GetOrganisation()
            GetOrganisationActivities()
            GetOutlet(xs:int OutletId)
            GetOutletActivities()
            GetReferenceData(xs:string ReferenceDataCode)
            GetSession(xs:string CaseId, xs:string SessionId)
            GetUser()
            Ping()
            SearchCase(ns9:CaseSearchCriteria Criteria)
            SearchClient(ns11:ClientSearchCriteria Criteria)
            UpdateCase(ns9:CaseDetailEditable Case, ns4:ArrayOfCaseClient Clients)
            UpdateClient(ns11:ClientBusinessDataExtended Client)
            UpdateClientAssessments(ns8:ClientAssessment ClientAssessment)
            UpdateOutlet(xs:int OutletId, ns10:OutletDetailsExtended OutletDetails)
            UpdateSession(xs:string CaseId, ns4:SessionDetailsExtended Session)
            UpdateSessionAssessments(ns8:SessionAssessment SessionAssessment)
            ValidateForDuplicateClient(ns11:DuplicateClientSearchCriteria Criteria)
         Types (123):
            ns0:ABN
            ns10:ActivitySpecificRequirement
            ns10:ActivitySpecificRequirements
            ns10:ArrayOfActivitySpecificRequirement
            ns9:ArrayOfCase
            ns4:ArrayOfCaseClient
            ns4:ArrayOfCaseId
            ns9:ArrayOfCaseSearchRecord
            ns4:ArrayOfCaseSessions
            ns11:ArrayOfClient
            ns11:ArrayOfClientBusinessDataExtended
            ns4:ArrayOfClientId
            ns11:ArrayOfClientIdWithTransaction
            ns10:ArrayOfOrganisation
            ns10:ArrayOfOutlet
            ns10:ArrayOfOutletActivity
            ns12:ArrayOfReferenceData
            ns10:ArrayOfServiceType
            ns13:ArrayOfSession
            ns4:ArrayOfSessionId
            ns11:ArrayOfStringDisabilities
            ns8:Assessment
            ns12:AssessmentReferenceDetail
            ns8:Assessments
            ns10:AvailableAssessmentType
            ns10:AvailableAssessmentTypes
            ns9:Case
            ns4:CaseClient
            ns9:CaseDetail
            ns9:CaseDetailBase
            ns9:CaseDetailEditable
            ns4:CaseExtendedDetails
            ns9:CaseSearchCriteria
            ns9:CaseSearchRecord
            ns9:CaseSearchSortColumns
            ns11:Client
            ns8:ClientAssessment
            ns11:ClientBusinessData
            ns11:ClientBusinessDataExtended
            ns4:ClientExtended
            ns11:ClientIdWithTransaction
            ns11:ClientSearchCriteria
            ns11:ClientSearchCriteriaBase
            ns11:ClientSearchSortColumns
            ns4:ClientSessions
            ns0:ConsentType
            ns10:DeliveryPartner
            ns10:DeliveryPartners
            ns12:Domain
            ns12:Domains
            ns11:DuplicateClientSearchCriteria
            ns0:ExceptionMessage
            ns10:ExtendedOrganisation
            ns13:ExtraItems
            ns0:Fault
            ns0:FaultCategory
            ns0:GetSiebelDataRequest
            ns0:Header
            ns0:ListAsOfDateInput
            ns0:LogMessage
            ns0:Message
            ns0:MessageFlow
            ns0:MessageLevel
            ns0:MessageList
            ns0:Month
            ns0:Note
            ns10:Organisation
            ns10:OrganisationActivities
            ns10:OrganisationActivity
            ns10:OrganisationActivityExtendedDetail
            ns10:OrganisationActivityList
            ns13:Outcome
            ns10:Outlet
            ns10:OutletActivities
            ns10:OutletActivitiesBasic
            ns10:OutletActivity
            ns10:OutletActivityBasic
            ns10:OutletDetails
            ns10:OutletDetailsExtended
            ns0:PagingControlInput
            ns0:PagingControlOutput
            ns9:ParentingAgreementOutcome
            ns0:ProcessedTransaction
            ns4:PropertyAgreementOutcomeType
            ns9:PropertyAgreementOutcomeType
            ns0:PublishMetaData
            ns13:Purposes
            ns4:ReasonForAssistance
            ns4:ReasonsForAssistance
            ns12:ReferenceData
            ns13:Referral
            ns13:ReferralOutType
            ns13:Referrals
            ns12:ScoreWithDescription
            ns8:Scores
            ns12:ScoresWithDescription
            ns11:SearchCriteria
            ns3:SearchCriteriaBase
            ns9:Section60I
            ns0:ServiceInfo
            ns10:ServiceType
            ns10:ServiceTypeSpecificRequirement
            ns10:ServiceTypeSpecificRequirements
            ns10:ServiceTypes
            ns13:Session
            ns8:SessionAssessment
            ns4:SessionClient
            ns4:SessionClientExtended
            ns4:SessionClients
            ns4:SessionClientsExtended
            ns13:SessionDetails
            ns4:SessionDetailsExtended
            ns4:SessionExtended
            ns13:SessionOutcomeDetail
            ns0:SortControl
            ns0:SortExpression
            ns0:SortablePageable
            ns11:Tags
            ns0:TransactionResult
            ns0:TransactionStatus
            ns0:TransactionStatusCode
            ns7:UnstructuredAddress
            ns10:User
```

Stay tuned...
