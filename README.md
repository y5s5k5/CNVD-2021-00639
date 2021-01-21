Experimental environment: win10 x64    
Software official website:http://pc.rising.com.cn
Software version:25.0.7.31    
Affected Component: ravmond.exe C:\Program Files (x86)\Rising\Rav\logfiles\ravmond.exe.rsnetsvr.log   
  
The vulnerability point is after the administrator installs Rising antivirus software,
Will automatically start a process named ravmond.exe continuously under the current user
C:\Program Files (x86)\Rising\Rav\logfiles\ravmond.exe.rsnetsvr.log
Write content

Logfiles are fully controlled even by ordinary users

Attackers can use symbolic links to write content to any file that has system permissions and has system permissions (cannot control the content).
If the target file is pci.sys, the computer will not start.
If you write an antivirus protection program, the antivirus protection will be ignored.

To exploit this vulnerability, you need to delete the logfiles directory, then create an object manager symbolic link so that \RPC Control\ravmond.exe.rsnetsvr.log points to the file name to be opened, and then create a directory link logfiles link to \RPC Control to write the target file.

For example, the cmd command:    
CreateSymlink.exe "C:\Program Files (x86)\Rising\Rav\logfiles\ravmond.exe.rsnetsvr.log" "‪C:\Windows\win.ini"    
