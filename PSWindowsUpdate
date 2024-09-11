try 
{ 
    # Check if NuGet provider is installed
    if (Get-PackageProvider | Where-Object { $_.Name -eq "NuGet" }) 
    { 
        Write-Output "NuGet Module already exists" 
    } 
    else 
    { 
        Write-Output "Installing NuGet module" 
        Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force 
    } 

    # Check if PSWindowsUpdate module is installed
    if (Get-Module -ListAvailable | Where-Object { $_.Name -eq "PSWindowsUpdate" }) 
    { 
        Write-Output "PSWindowsUpdate module already exists" 
    } 
    else 
    { 
        Write-Output "Installing PSWindowsUpdate Module" 
        Install-Module PSWindowsUpdate -Force 
    } 

    # Import the PSWindowsUpdate module
    Import-Module -Name PSWindowsUpdate 

    Write-Output "Starting update -->" + (Get-Date -Format "dddd MM/dd/yyyy HH:mm")  
    
    # Install the specific Windows Security Update
    Install-WindowsUpdate -KBArticleID [ARTICLEID] -AcceptAll -ForceDownload -ForceInstall -IgnoreReboot 

    Write-Output "Update completed -->" + (Get-Date -Format "dddd MM/dd/yyyy HH:mm") 
} 
catch 
{ 
    Write-Output $_.Exception.Message 
}
