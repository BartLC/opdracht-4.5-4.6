maak een passende comment base helpfile voor je loginscript en een loginscript aanmaken

<#  
 
.SYNOPSIS      
 logonscript wordt uitgevoerd bij het aanmelden
 
.DESCRIPTION   
 Dit script maakt een logbestand aan met
   - Gebruikersnaam
   - Computernaam
   - Datum en tijd
   - IPAdres
 elke keer als een gebruiker aanmeldt.
 
.NOTES         
 Naam: 
#>
$CompName = get-content ENV:ComputerName
$UserName = get-content ENV:UserName
$Date = get-date -Format "dd-MM-yyyy HH:mm"
$FileName = get-date -Format yyyyMM
$IPAddress = Get-NetIPAddress -IPAddress 10.0.6.*|Select-Object -ExpandProperty IPaddress
$Text = "Logon: " + $UserName + " " + $CompName + " " + $Date + " " + $IPAddress
$Text|Out-File -Append -FilePath C:\USERS\ll-81621\Documents\$Filename.txt

