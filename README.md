# Active Roles Attestation
Attestation Functionality for One Identity Active Roles

Using the Add-on Manager, import this package to add Group Membership Attestation to your Active Roles installation!  Simply copy the file to a server with the Active Roles Console and Add-On Manager installed, and double-click to automatically launch the Add-On Manager and import the package.  Alternatively, you can navitate to the Add-On Manager inside the Active Roles Console, and manually select the package to import from there.

# Objects Imported
Virtual Attributes:
  AttestationRequired - Boolean
  Attested - Boolean
  LastAttestationDate - GeneralizedTime
  AttestationHistory - DirectoryString (Multi-valued Attribute)

Workflows:
  Container: Attestation Engine
    Expiration Schedule - Scheduled
    Notify Group Owners - Scheduled
    Process Attestation - Change Based

Access Templates:
  Container: Attestation
    Attest Group
    Attestation Required

Web Interface Customizations:
  
