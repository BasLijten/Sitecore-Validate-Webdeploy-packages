# How to use this Module:

1. copy ValidatePackage.psm1 and ValidatePackage.psd1 to $home\Documents\WindowsPowerShell\Modules\ValidatePackage (or any other powershell location)
2. Open a new powershell prompt and type: Import-Module ValidatePackage
3. Create one or more Sitecore baseline directories, with the following subfolders: Installation, Modules and WebDeploy. For example:  
&nbsp;+ baseline  
&nbsp;&nbsp;&nbsp;+ sitecore 8.0 update 5  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;+ Installation  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;+ Modules  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;+ WebDeploy  
&nbsp;&nbsp;&nbsp;+ sitecore 8.1 update 1  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;+ Installation  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;+ Modules  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;+ WebDeploy  

  * Installation: Sitecore baseline zip: or the zip from dev.sitecore.net, or a zip file that is created from your freshly installed sitecore directory
  * Modules: Place all installed sitecore modules (not implemented yet)
  *	WebDeploy: Place all shared web deploy packages in this directory, not the site or project specific ones!
	
	These files are not subject to change often, and is a stable base for your projects
4. Create a Sitecore instance specific directory, this directory contains all the web deploy packages that are deployed to a specific instance (and are not part of the baseline)
5. Create 4 directories beneath:
	D, T, A, P (Development, Test, Acceptance, Production). Place the latest instance specific web deploy packages in these directories. These files may change often on Development, but may have a slower lifecycle on Production

6. Run: 
```PowerShell
Validate-WebDeployPackage -BaselineDirectory "C:\baseline\sc 8.0 update 5\" -InstanceSpecificWebDeployPackagesDirectory "c:\instanties\ODV\"  -WebdeployPackageToValidate "C:\sitecore packages\custom package.zip" -Environment "D"
```

a report is generated on what files are duplicated, and in case of assemblies, what version is the baseline version and what version will be deployed. Source location is available as well. Happy usage!

