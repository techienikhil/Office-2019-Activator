@echo on
title Activate Microsoft Office 2019 !
cls
echo ============================================================================
echo #Project: Activating Microsoft software products
echo ============================================================================
echo.
echo #Supported products:
echo - Microsoft Office Standard 2019
echo - Microsoft Office Professional Plus 2019
echo.
echo.
(if exist "%ProgramFiles%\Microsoft Office\Office16\ospp.vbs" cd /d "%ProgramFiles%\Microsoft Office\Office16")
(if exist "%ProgramFiles(x86)%\Microsoft Office\Office16\ospp.vbs" cd /d "%ProgramFiles(x86)%\Microsoft Office\Office16")
(for /f %%x in ('dir /b ..\root\Licenses16\ProPlus2019VL*.xrm-ms') do cscript ospp.vbs /inslic:"..\root\Licenses16\%%x" >nul)
(for /f %%x in ('dir /b ..\root\Licenses16\ProPlus2019VL*.xrm-ms') do cscript ospp.vbs /inslic:"..\root\Licenses16\%%x" >nul)
echo.
echo ============================================================================
echo Activating your Office...
cscript //nologo slmgr.vbs /ckms >nul
cscript //nologo ospp.vbs /setprt:1688 >nul
cscript //nologo ospp.vbs /unpkey:6MWKP >nul
cscript //nologo ospp.vbs /inpkey:NMMKJ-6RK4F-KMJVX-8D9MJ-6MWKP >nul
set i=1
:server
if %i%==1 set KMS_Sev=kms.03k.org
if %i%==2 set KMS_Sev=kms.03k.org
if %i%==3 set KMS_Sev=kms.03k.org
if %i%==4 goto notsupported
cscript //nologo ospp.vbs /sethst:%KMS_Sev% >nul
echo ============================================================================
echo.
echo.
cscript //nologo ospp.vbs /act | find /i "successful" 

 (echo.
echo ============================================================================
echo #Please feel free to contact me at mail2ehsanalem@gmail.com if you have any questions or concerns.
echo ============================================================================
choice /n /c YN /m "Would you like to visit my Page [Y,N]?" 
 if errorlevel 2 exit) || (echo The connection to my KMS server failed! Trying to connect to another one... 
 echo Please wait... 
 echo. 
 echo. 
 set /a i+=1 
 goto server)
explorer "http://github.io/agileehsan"
goto halt
:notsupported
echo.
echo ============================================================================
echo Sorry! Your version is not supported.
echo.
:halt
pause >nul