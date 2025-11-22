# ULH
User Land Hooking Demo for Intrustion Detection Course.

Compiled driver from https://github.com/wbenny/injdrv with a self signed cert.

Remember your installing a driver from a random github page. Please do not do this on your personal machine. Use a VM.

To run:
1. Disable secure-boot
2. Run from a administrative prompt
```
bcdedit /set nointegritychecks on
bcdedit.exe -set testsigning on
```
3. Import the Cert
```
 $pwd = ConvertTo-SecureString -String "P@ssw0rd123!" -Force -AsPlainText

# Import into LocalMachine\My (private key store)
 Import-PfxCertificate `
  -FilePath "PATHTO\injdrvtest.pfx" `
   -CertStoreLocation "Cert:\LocalMachine\My" `
   -Password $pwd

 # Import into Trusted Root
 Import-PfxCertificate `
   -FilePath "PATHTO\injdrvtest.pfx" `
   -CertStoreLocation "Cert:\LocalMachine\Root" `
   -Password $pwd

 # Import into Trusted Publishers
 Import-PfxCertificate `
   -FilePath "PATHTO\injdrvtest.pfx" `
   -CertStoreLocation "Cert:\LocalMachine\TrustedPublisher" `
   -Password $pwd
```
4. Follow along with the lecture.
