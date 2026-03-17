---
Type: "[[Processes]]"
date: 2026-02-26
tags:
  - Azure
  - MgGraph
  - Certificate
---
# Context
Sometimes, you need to connect to Azure using a MgGraph application.
This can allow you to have access to logs using powershell for examples.
To do so, you can use a certificate which is a cleaner way to do.
# Steps

## Generate a self-signed certificate
```Powershell
$cert = New-SelfSignedCertificate `  
    -Subject "CN=GraphAppCert" `  
    -CertStoreLocation "Cert:\CurrentUser\My" `  
    -KeySpec Signature `  
    -KeyLength 2048 `  
    -KeyExportPolicy Exportable `  
    -HashAlgorithm SHA256 `  
    -NotAfter (Get-Date).AddYears(1)
    
    Export-Certificate `  
    -Cert $cert `  
    -FilePath "C:\Temp\MgGraph_Cert.cer"
    
    $pwd = ConvertTo-SecureString -String "ThisIsAStrongPassword" -Force -AsPlainText
```

You then need to export the certificate as a `.pfx` in the machine you're using : 
```Powershell
Export-PfxCertificate `  
    -Cert $cert `  
    -FilePath "C:\Temp\MgGraph_Cert.pfx" `  
    -Password $pwd
```

Once it's done, you should have in your `C:\Temp\` folder your certificate with both `.cer` and `.pfx` files.

You should then import the cert in your datastore (remember to change the password with the secure string you got earlier)
```Powershell
$pwd = ConvertTo-SecureString "TheSecureStringYouGotEarlier" -AsPlainText -Force
 
Import-PfxCertificate `
    -FilePath "C:\Temp\Secu_Graph.pfx" `
    -CertStoreLocation "Cert:\CurrentUser\My" `
    -Password $pwd
```

## Connect to MgGraph with the certificate
You can then connect to the MgGraph datastore using the ClientId, TenantId and CertificateThumbprint
You can find the CLientId and TenantId in the overview of your app in Azure
The thumbprint is obtained when opening the certificate in the last entry of the details tab.
```Powershell
Connect-MgGraph -ClientID "<ClientId>" -TenantId "<TenantId>" -CertificateThumbprint "<Thumbprint>"
```
Once done, you're connected as the MgGraph app and can do queries using the rights given to the app.
