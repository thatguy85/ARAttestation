# Active Roles Attestation Readme
## Attestation Functionality for One Identity Active Roles

Using the Add-on Manager, import this package to add Group Membership Attestation to your Active Roles installation!  Simply copy the file to a server with the Active Roles Console and Add-On Manager installed, and double-click to automatically launch the Add-On Manager and import the package.  Alternatively, you can navigate to the Add-On Manager inside the Active Roles Console, and manually select the package to import from there.

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

**IMPORTANT!!**  Prior to modifying any settings, it is important to make sure the newly imported workflows are disabled.  If they aren't, simply select the workflows inside the Attestation Engine folder, right click and disable.  This prevents anything from running before you're ready to push this functionality to a wider audience.
