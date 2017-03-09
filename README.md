# CATAzureStackRepo

Once you have deployed Azure Stack, log in as Service admin.  At this time (not ready as yet) you will need
to install the resource providers using the instructions here in the Use Services section.

Now that is done, we can start the configuration of the lab.  The script will do the following:

 - Install the correct version of Azure RM and Azure Stack PowerShell
 - Install the Azure Stack Tools 
 - Add two images to the PIR:  Windows Server 2016 / Ubuntu
 - Create plans, offers, and quotas with specific quotas aligned to offers and plans
 - Configure delegation plan and offer  You will need to add your users to delegation and subscriptions using the instructions here
 - Create a custom tag for use with the Server 2016 imageConfigure Marketplace Syndication 
   **NOTE:  You must download the Windows Server 2016 Eval ISO either from TechNet or as part of the installation of Azure
Stack.  You will need to provide the full path to the ISO. 

The deployment requires one of two scripts that you can save to a location on the
host.   
BuildLab_Ent.ps1: Creates an enterprise solution that includes four business units; HR, Finance, IT, and Development
BuildLab_ServiceProvider.ps1: Creates a service provider lab with public offers; Premium, Standard, Trial 

NOTE: at this time no RP's are available 


Instructions

1    Copy either the Enterprise or Service provider script from GitHub and save to your machine, saving as a ps1 file.  

2    Run the following command to get your subscription id

        Get-AzureRMContext

3    In the Enterprise / Service provider lab file, change following values to the ones applicable to your lab.  Save the PS1 file

        MUST be run from HOST Server
   
        Requires -RunAsAdministrator
  
        $ISOPath = '<PATH>\14393.0.161119-1705.RS1_REFRESH_SERVER_EVAL_X64FRE_EN-US.ISO'  #Change to the location where you saved the ISO for Server 2016
     
        $AADTenantDomain = 'YOURDOMAIN.ONMICROSOFT.COM'
   
        $ServiceAdminUsername = 'SERVICE ADMIN ACCOUNT'
   
        $ServiceAdminPassword = 'SERVICE ADMIN PASSWORD!'
   
        $AzureAD = "YOURBILLINGDOMAIN.ONMICROSOFT.COM"
   
        $AzureSubID = "YOURBILLLINGDOMAIN GUID"
   
        $UserAccountName = "YOURBILLLING DOMAIN OWNER"

 
  
  NOTE: do not change the variables below!!!!

        $MASDomain ='local.azurestack.external'
   
        $AdminUri = 'https://api.{0}' -f $MASDomain
   
        $ArmLocation='local'
   
        $OfferRG='OffersandPlans'
   
        $DelegatedOffersRG='CASDelegatedOffers'

 

4    Run the Enterprise/Service provider script to install the lab

NOTE: you may be asked to provide credentials during the build of the lab.

NOTE: Due to the length of time the script runs, you may need to reauthenticate.  Before installation of each of the images
(end of script), a reauthentication to azure stack will occur automatically

 

 

 

 

 

 

 

 

