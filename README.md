# Active Roles Attestation Readme
## Attestation Functionality for One Identity Active Roles

Add basic group membership attestation functionality to Active Roles!  This package uses a combination of workflows, virtual attributes, and customized web interfaces to achieve this.  Everything in this package is done using built-in functionality, which means that it is fully supported by One Identity.  There is no custom coding!  Please read instructions fully prior to installing anything.

# Objects Imported
## Virtual Attributes:
    AttestationRequired - Boolean
    Attested - Boolean
    LastAttestationDate - GeneralizedTime
    AttestationHistory - DirectoryString (Multi-valued Attribute)

## Workflows:
###  Container: Attestation Engine
    Expiration Schedule - Scheduled
    Notify Group Owners - Scheduled
    Process Attestation - Change Based

## Access Templates:
 ### Container: Attestation
    Attest Group
    Attestation Required

## Web Interface:
    Attestation (alias)

## Web Interface Customizations:
    Certify Access (command)
    Attestation Process (form)
    Attestation (tab)
    members (entry)
    Attested (entry)
    Custom Text Field
    Custom Text Field

# Instructions

Website installation:
1.  Open the Active Roles Configuration Center, navigate to the Web Interface tab, then click Create.
2.  Give the website an Alias.  We suggest 'Attestation'
3.  For Configuration, click the drop-down menu and select 'Import from a file' and select the configuration file included in this download 'Attestation Configuration(8.2)'

**IMPORTANT!!**  Prior to modifying any settings, it is important to make sure the newly imported workflows are disabled.  If they aren't, simply select the workflows inside the Attestation Engine folder, right click and disable.  This prevents anything from running before you're ready to push this functionality to a wider audience.

Active Roles Configuration:
1. Import the add-on manager package by either double-click on it on the server that hosts Active Roles, or open the Add-On manager and import the package.
2.  After importing the package via Add-On Manager, begin by verifying the successful import of all the objects listed above.  Navigate to the new web interface as any AR user which should be https://YOURSERVER/Attestation
3.  Review the following explanations of the workflows and their purpose before configuring the workflows and replace the placeholders so that the attestation works in the way you want it to.
  -  Expiration Schedule - This is a scheduled workflow that is configured to run every day.  The workflow performs a search for all groups which require attestation 'AttestationRequired = True' and have either no previous attestation on record 'Attested = NULL' or the previous attestation performed was 6 or more months ago 'LastAttestationDate >= CurrentDate - 182 days'.  Change this formula to expire attestations on the schedule you require.  Once this is done, it expires the Attestation 'Attested = False'
  -  Notify Group Owners - This workflow is scheduled to run every day.  It simply searches for groups that require attestation 'AttestationRequired = True' and 'Attested = False'.  It sends an email to the owner of the group found by the search.  The email contains an embeedded URL to the Attestation webpage.  Modify this URL and the email contentsto your specific requirements.
  -  Process Attestation - This workflow is executed whenever the "Attested" attribute for any group object is changed.  If the change is made by the active roles service account (replace this value with your service account) then it records the change as made by the "System" in the AttestationHistory attribute.  If anyone else modifies the value, we append the AttestationHistory attribute with a line that says "Attested by (user) on (date)"
    
