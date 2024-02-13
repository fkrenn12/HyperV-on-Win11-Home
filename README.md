# HyperV-on-Win11-Home

###Windows 11 Home do not have Hyper-V support installed.

Copy the following lines into a self created .bat file.

```sh
pushd "%~dp0"
dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hv.txt
for /f %%i in ('findstr /i . hv.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"
del hv.txt
Dism /online /enable-feature /featurename:Microsoft-Hyper-V -All /LimitAccess /ALL
pause
```

Save the file and execute it with administrator pivileges.<br>
Then restart the computer adn use Features to aktivate Hyper-V.

