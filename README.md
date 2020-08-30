# registry
# MS DOS 

- “config.sys” and “autoexec.bat”. 

- “Config.sys” was used to load the device drivers and 

- “autoexec.bat” was used to store the configurations of running programs and other environmental variables

- two files used in MS-DOS were replaced by INI files. These files were used to store the configuration settings of the computers.

- In Windows 95, a hierarchical database named Registry was introduced

  \2. THE WINDOWS REGISTRY BASICS

  ## Windows Registry 

  is a central repository or hierarchical database of configuration data for the
  operating system and most of its programs 

   It contains abundant information that has potential evidential value in forensic analysis 

  Windows Registry Editor can be used to access Windows Registry. Windows Registry Editor can be started by using the “run”
  command to run the “regedit.exe” file.

  • here are five root keys, 

  • HKEY_CLASSES_ROOT,                                  • HKEY_CURRENT_USER, 

  • HKEY_LOCAL_MACHINE,                              • HKEY_USERS,                                  • HKEY_CURRENT_CONFIG 

  Keys : this structure is just a logical structure • 

  Among these five root keys, only two root keys, These two keys are called master keys. HKEY_LOCAL_MACHINE 

  HKEY_USERS,

  ![image-20200830040731406](C:\Users\Mohamed ElSaman\AppData\Roaming\Typora\typora-user-images\image-20200830040731406.png)

The other three keys are derived keys since they are derived from the two master keys and their subkeys . 

##### HKEY_LOCAL_MACHINE ( HKLM) •

It contains all of the configuration settings of a computer. 

 When a computer startups, the local machine settings will boot before the individual user settings.

 • Five Hives are : HARDWARE, SAM, SECURITY, SOFTWARE, and  SYSTEM.![image-20200830041002280](C:\Users\Mohamed ElSaman\AppData\Roaming\Typora\typora-user-images\image-20200830041002280.png)

HARDWARE is used to store the information of hardware devices that a computer detects when the computer starts up. So, the subkeys in HARDWARE are also created during the booting process. 

• SAM is the abbreviation of Security Account Manager which is a local security database. Subkeys in SAM contain the setting data of users and work groups.

• SECURITY includes a local security database in SAM and a strict ACL is used to manage the users who could access the database. 

• SOFTWARE includes all of the configuration settings of programs. Information on the programs is stored in a standard format: HKLM\Software\Vendor\Program\Version. 

• SYSTEM contains the configuration settings of hardware drivers and services. The key path is HKEY_LOCAL_MACHINE\SYSTEM\ControlSetXXX, where XXX is a three digital number from 000,

##### HKEY_USERS (HKU) 

• HKU is another master key. It contains all of the per-user settings • current console user and other users who logged on this computer before 

 3 Basic Sub keys   

Defult  , SID  , SID_Classes

• Usually, we could see

 • S-1-5-18, Local System Account 

• S-1-5-19, Local Service Account,

 • S-1-5-20, Network Service Account

![image-20200830041335142](C:\Users\Mohamed ElSaman\AppData\Roaming\Typora\typora-user-images\image-20200830041335142.png)

##### HKEY_CLASSES_ROOT (HKCR). 

HKCR contains two keys: 

HKLM\SOFTWARE\Classes & HKCU\Software\Classes

HKCU links to a subkey of HKU, HKU\SID. 

This key allows all of the Windows programs and applications to create, access, modify, and store the information of current console user without determining which user is logging in.

 Have basic 5 Subkeys

• **Environment** is about the environmental configurations. 

• **Identities** are related to Outlook Express. 

• **Network** contains settings to connect the mapped network drive. 

• **Software** refers to the user application settings. 

• **Volatile Environment** is used to define the environmental variables according to different users who logon a computer

![image-20200830041622498](C:\Users\Mohamed ElSaman\AppData\Roaming\Typora\typora-user-images\image-20200830041622498.png)

##### HKEY_CURRENT_CONFIG (HKCC). 

• HKCC is an image of the hardware configuration profiles. HKLM\SYSTEM\Current\ControlS et\Hardware\Current, is also a link to HKLM\SYSTEM\ControlSet\Hard ware Profiels\XXXX, where XXXX is a four digital number from 0000.

Values 

• Just like a file of Windows, a value also has its properties. Name, type, and data are the three components of a value. Every value has a unique name. The naming regulations are also similar to those of files. Some special characters such as “?”, “\”, and so on could not appear in the name of a value. 

• here are six major types of values: string, multistring, expandable string, binary, Dword, and Qword

• String values are the easiest to understand because data in this type is recorded in plain text in English. 

• Multistring values include a list of strings with ASCII code 00 separating these strings. 

• Expandable string is another variant of string value. Expandable string contains special variables such as %SYSTEMROOT%, %USERPROFILE% and so on. These variables could replace some special path easily. For example, if we want to locate the folder X:\Documents and Settings\username\Desktop, 

• The %USERPROFIEL%\Desktop could be used no matter on which drive windows are installed and which user logs on.

• Binary value also stores string but the data is displayed in hex format and the information stored is always related to hardware. 

• Unlike the above value types, the data stored in Dword and Qword are not strings of characters. There are two numbers in Dword and Qword types: 1 and 0 (usually 1 for enable and 0 for disable). In some cases, numbers within 60 are used to indicate data related to timeout settings. However, the difference between Dword and Qword is that Dword stores 32-bit data and Qword stores 64-bit data

• If we use forensic tools to view the Windows Registry in an offline environment or view the Registry remotely, only the two master keys will be listed. So only the two master keys and their subkeys have hives. The hives of HKLM’s subkeys are stored at %SYSTEMROOT%System32\config, and the hives of HKU’s subkeys are stored at %USERPFOFILE%

