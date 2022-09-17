@ECHO OFF
color 0A
:: Check for permissions
title Getting Permission
>nul 2>&1 "%SYSTEMROOT%\system32\cacls.exe" "%SYSTEMROOT%\system32\config\system"

:: If error flag set, we do not have admin.
if '%errorlevel%' NEQ '0' (
Echo Requesting administrative privileges...
goto UACPrompt
) else ( goto gotAdmin )

title Disableling UAC
:UACPrompt
Echo Set UAC = CreateObject^("Shell.Application"^) > "%temp%\getadmin.vbs"
Echo UAC.ShellExecute "%~s0", "", "", "runas", 1 >> "%temp%\getadmin.vbs"

"%temp%\getadmin.vbs"
Exit /B


title Got Admin Rights
:gotAdmin
if exist "%temp%\getadmin.vbs" ( Del "%temp%\getadmin.vbs" )
Pushd "%CD%"
CD /D "%~dp0"
ECHO OFF
CLS
:MENU
title Borcherds Tech
CLS
echo     ____                      __                     __         ______             __  
echo    / __ ) ____   _____ _____ / /_   ___   _____ ____/ /_____   /_  __/___   _____ / /_ 
echo   / __ / / __ \ / ___// ___// __ \ / _ \ / ___// __  // ___/    / /  / _ \ / ___// __ \
echo  / /_/ // /_/ // /   / /__ / / / //  __// /   / /_/ /(__  )    / /  /  __// /__ / / / /
echo /_____/ \____//_/    \___//_/ /_/ \___//_/    \__,_//____/    /_/   \___/ \___//_/ /_/ 
ECHO .......................................................................................
ECHO PRESS 1, 2 OR 3 to select your task, or 0 to EXIT.
ECHO .......................................................................................
ECHO.
ECHO 1 - System File Checker tool to repair missing or corrupted system files
ECHO 2 - RestoreHealth Windows Image Health Online
ECHO 3 - Backup
ECHO 0 - EXIT
ECHO.
SET /P M=Type 1, 2, 3, or 0 then press ENTER:
IF %M%==1 GOTO SFC
IF %M%==2 GOTO DISM
IF %M%==3 GOTO Backup
IF %M%==0 exit

:SFC
cls
title System File Checker
sfc /scannow

GOTO MENU

:DISM
cls
title RestoreHealth Windows Image Health
dism /Online /Cleanup-Image /RestoreHealth

GOTO MENU

:Backup
cls
title  Backup
:---------------------------------------------------------------------------------------

::Detect OS
title Detecting OS

mkdir "%~dp0\[Backup]\%USERNAME%\"
echo Creating Backup Directory

:Backup
setlocal
for /f "tokens=4-5 delims=. " %%i in ('ver') do set VERSION=%%i.%%j

echo Detecting OS...

if "%version%" == "10.0" Goto Win10
if "%version%" == "6.3" Goto Win8
if "%version%" == "6.2" Goto Win8
if "%version%" == "6.1" Goto Win7
if "%version%" == "6.0" Goto WinV
if "%version%" == "5.1" Goto WinXP
if "%version%" == "5.2" Goto WinXP

rem etc etc
endlocal


:Win10
echo Windows 10
cls

Echo Backing up Opera...
Echo off
xcopy "c:\Users\%username%\AppData\Local\Opera Software" "%~dp0\[Backup]\%USERNAME%\AppData\Local\Opera Software" /D /E /C /R /H /I /K /Y 
xcopy "c:\Users\%username%\AppData\Roaming\Opera Software" "%~dp0\[Backup]\%USERNAME%\AppData\Roaming\Opera Software" /D /E /C /R /H /I /K /Y 
cls

Echo Backing up Chrome...
Echo off
xcopy "c:\Users\%username%\AppData\Local\Google" "%~dp0\[Backup]\%USERNAME%\AppData\Local\Google" /D /E /C /R /H /I /K /Y 
xcopy "c:\Users\%username%\AppData\Roaming\Google" "%~dp0\[Backup]\%USERNAME%\AppData\Roaming\Google" /D /E /C /R /H /I /K /Y 
cls

Echo Backing up Documents...
Echo off
xcopy "c:\Users\%username%\Documents" "%~dp0\[Backup]\%USERNAME%\Documents" /D /E /C /R /H /I /K /Y
cls
Echo Backing up Contacts...
Echo off
xcopy "c:\Users\%username%\Contacts" "%~dp0\[Backup]\%USERNAME%\Contacts" /D /E /C /R /H /I /K /Y
cls
Echo Backing up Downloads...
Echo off
cls
xcopy "c:\Users\%username%\Downloads" "%~dp0\[Backup]\%USERNAME%\Downloads" /D /E /C /R /H /I /K /Y
Echo Backing up Favorites...
Echo off
cls
xcopy "c:\Users\%username%\Favorites" "%~dp0\[Backup]\%USERNAME%\Favorites" /D /E /C /R /H /I /K /Y
Echo Backing up Links...
Echo off
cls
xcopy "c:\Users\%username%\Links" "%~dp0\[Backup]\%USERNAME%\Links" /D /E /C /R /H /I /K /Y
Echo Backing up Music...
Echo off
cls
xcopy "c:\Users\%username%\Music" "%~dp0\[Backup]\%USERNAME%\Music" /D /E /C /R /H /I /K /Y
Echo Backing up Pictures...
Echo off
cls
xcopy "c:\Users\%username%\Pictures" "%~dp0\[Backup]\%USERNAME%\Pictures" /D /E /C /R /H /I /K /Y
Echo Backing up Saved Games...
Echo off
cls
xcopy "c:\Users\%username%\Saved Games" "%~dp0\[Backup]\%USERNAME%\Saved Games" /D /E /C /R /H /I /K /Y
Echo Backing up Searches...
Echo off
cls
xcopy "c:\Users\%username%\Searches" "%~dp0\[Backup]\%USERNAME%\Searches" /D /E /C /R /H /I /K /Y
Echo Backing up Videos...
Echo off
cls
xcopy "c:\Users\%username%\Videos" "%~dp0\[Backup]\%USERNAME%\Videos" /D /E /C /R /H /I /K /Y
Echo Backing up Desktop...
Echo off
cls
xcopy "c:\Users\%username%\Desktop" "%~dp0\[Backup]\%USERNAME%\Desktop" /D /E /C /R /H /I /K /Y
cls

Echo Backing up Taiga...
Echo off
xcopy "c:\Users\%username%\AppData\Roaming\Taiga" "%~dp0\[Backup]\%USERNAME%\AppData\Roaming\Taiga" /D /E /C /R /H /I /K /Y 
cls

Goto END

:Win8
echo Windows 8
Goto END

:Win7
echo Windows 7
@ECHO OFF

:Opera
xcopy "c:\Users\%username%\AppData\Local\Opera Software" "%~dp0\[Backup]\%USERNAME%\AppData\Local\Opera Software" /D /E /C /R /H /I /K /Y 
xcopy "c:\Users\%username%\AppData\Roaming\Opera Software" "%~dp0\[Backup]\%USERNAME%\AppData\Roaming\Opera Software" /D /E /C /R /H /I /K /Y 

:Chrome
xcopy "c:\Users\%username%\AppData\Local\Google" "%~dp0\[Backup]\%USERNAME%\AppData\Local\Opera Software" /D /E /C /R /H /I /K /Y 
xcopy "c:\Users\%username%\AppData\Roaming\Google" "%~dp0\[Backup]\%USERNAME%\AppData\Roaming\Opera Software" /D /E /C /R /H /I /K /Y 

:Documents
xcopy "c:\Users\%username%\Documents" "%~dp0\[Backup]\%USERNAME%\Documents" /D /E /C /R /H /I /K /Y 
xcopy "c:\Users\%username%\Contacts" "%~dp0\[Backup]\%USERNAME%\Contacts" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Downloads" "%~dp0\[Backup]\%USERNAME%\Downloads" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Favorites" "%~dp0\[Backup]\%USERNAME%\Favorites" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Links" "%~dp0\[Backup]\%USERNAME%\Links" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Music" "%~dp0\[Backup]\%USERNAME%\Music" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Pictures" "%~dp0\[Backup]\%USERNAME%\Pictures" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Saved Games" "%~dp0\[Backup]\%USERNAME%\Saved Games" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Searches" "%~dp0\[Backup]\%USERNAME%\Searches" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Videos" "%~dp0\[Backup]\%USERNAME%\Videos" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Desktop" "%~dp0\[Backup]\%USERNAME%\Desktop" /D /E /C /R /H /I /K /Y

Goto END

:WinV
echo Windows Vista
@ECHO OFF

:Opera
xcopy "c:\Users\%username%\AppData\Local\Opera Software" "%~dp0\[Backup]\%USERNAME%\AppData\Local\Opera Software" /D /E /C /R /H /I /K /Y 
xcopy "c:\Users\%username%\AppData\Roaming\Opera Software" "%~dp0\[Backup]\%USERNAME%\AppData\Roaming\Opera Software" /D /E /C /R /H /I /K /Y 

:Chrome
xcopy "c:\Users\%username%\AppData\Local\Google" "%~dp0\[Backup]\%USERNAME%\AppData\Local\Opera Software" /D /E /C /R /H /I /K /Y 
xcopy "c:\Users\%username%\AppData\Roaming\Google" "%~dp0\[Backup]\%USERNAME%\AppData\Roaming\Opera Software" /D /E /C /R /H /I /K /Y 

:Documents
xcopy "c:\Users\%username%\Documents" "%~dp0\[Backup]\%USERNAME%\Documents" /D /E /C /R /H /I /K /Y 
xcopy "c:\Users\%username%\Contacts" "%~dp0\[Backup]\%USERNAME%\Contacts" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Downloads" "%~dp0\[Backup]\%USERNAME%\Downloads" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Favorites" "%~dp0\[Backup]\%USERNAME%\Favorites" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Links" "%~dp0\[Backup]\%USERNAME%\Links" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Music" "%~dp0\[Backup]\%USERNAME%\Music" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Pictures" "%~dp0\[Backup]\%USERNAME%\Pictures" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Saved Games" "%~dp0\[Backup]\%USERNAME%\Saved Games" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Searches" "%~dp0\[Backup]\%USERNAME%\Searches" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Videos" "%~dp0\[Backup]\%USERNAME%\Videos" /D /E /C /R /H /I /K /Y
xcopy "c:\Users\%username%\Desktop" "%~dp0\[Backup]\%USERNAME%\Desktop" /D /E /C /R /H /I /K /Y

Goto END

:WinXP
echo Windows XP

xcopy "c:\Documents and Settings\%username%\My Documents" "%~dp0\[Backup]\%USERNAME%\My Documents" /D /E /C /R /H /I /K /Y
xcopy "c:\Documents and Settings\%username%\Desktop" "%~dp0\[Backup]\%USERNAME%\Desktop" /D /E /C /R /H /I /K /Y
 
:END

GOTO MENU

:Done
Sleep 5

GOTO MENU 




