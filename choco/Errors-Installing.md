If you get this error:
Exception calling "DownloadFile" with "2" argument(s): "The underlying connection was closed: Could not establish trust relationship for 
the SSL/TLS secure channel."

Run this from PowerShell terminal:  [System.Net.ServicePointManager]::ServerCertificateValidationCallback = {$true}