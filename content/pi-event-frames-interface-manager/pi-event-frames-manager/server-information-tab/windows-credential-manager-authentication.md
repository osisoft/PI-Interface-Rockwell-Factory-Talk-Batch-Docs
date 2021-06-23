---
uid: windowscredentialmanagerauthentication
---

# Windows Credential Manager authentication

Batch interfaces use Windows Credential Manager for authentication, encrypting your user name and log in information so that you are not required to re-enter authentication information for subsequent log ins.
  
The .ini file includes PIUSECM, AFUSECM, and SOURCE.USECM flags that are set to False until your batch interface is run for the first time. After this point, the user name and password are stored in Windows Credential Manager, those .ini file flags are reset to True, thus authorizing your subsequent use of that machine without requiring you to reenter your log in credentials.
  
After this point the user name and password are stored in Windows Credential Manager your user name and password information is encrypted
Credentials are stored in Windows Credential Manager using the following format:
```
# code block
{interfacename}_{interfaceid}_{source}.
```
  
The {source} can be "PI", "AF", or can also be {source}_{index number}. For example, credential used for the Emerson DeltaV batch interface may be identified in Windows Credential Manager as:

*	EMDVB_1_PI for the PI Data server associated with the Emerson DeltaV batch interface
*	EMDVB_1_AF for the PI Asset Framework server associated with the Emerson DeltaV batch interface
*	EMDVB_1_Source_1 for the data source associated with the Emerson DeltaV batch interface

You can change log in credentials by modifying the batch interface configuration file. Windows Credential Manager automatically updates with the newly encrypted log in information, resetting the flags in the .ini file to True.