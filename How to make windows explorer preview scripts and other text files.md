[How to make windows explorer preview scripts and other text files](https://superuser.com/questions/1320812/how-to-make-windows-explorer-preview-scripts-and-other-text-files)


What worked for me was 2nd answer in the thread. Member user255627 points out the correct key is HKEY_LOCAL_MACHINE\SOFTWARE\Classes\.py which requires attribute PerceivedType   REG_SZ   text.

I created an attribute in this key with reg command. You can substitute .py with any extension type and enable a bunch of extensions this way. No need for a external program as mentioned in other thread.

from windows command prompt cmd.exe
`reg add HKLM\SOFTWARE\Classes\.py /v PerceivedType /t REG_SZ /d text`
If you don't have reg permissions to HKLM (local machine) you can use HKCU (current user)

reg add HKCU\SOFTWARE\Classes\.py /v PerceivedType /t REG_SZ /d text
You can query like this.

reg query HKLM\SOFTWARE\Classes\.py /s

HKEY_LOCAL_MACHINE\SOFTWARE\Classes\.py
(Default)    REG_SZ    Python.File
PerceivedType    REG_SZ    text
Thanks for the help guys. very useful.
