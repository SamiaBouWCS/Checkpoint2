### Exercice 2 : Débogage de script PowerShel
##### Question 2   

Dans la définition de $Users : 
`$Users = Import-Csv -Path $CsvFile -Delimiter ";" -Header "prenom","nom","societe","fonction","service","description","mail","mobile","scriptPath","telephoneNumber" -Encoding UTF8  | Select-Object -Skip 2`  

Modifier **Select-Object** `-Skip 2` par **`-Skip 1`** afin qu'il ne skipe que l'entête et non l'entête + la deuxième ligne qui est le premier utilisateur.  

##### Question 3 
Dans la partie $UserInfo ajouter un champ Description:
```  
  $UserInfo = @{
            Name                 = "$Prenom.$Nom"
            FullName             = "$Prenom.$Nom"
	    **Description          = $Description**
	Password             = $Password
            AccountNeverExpires  = $true
            PasswordNeverExpires = $false
        }
```

##### Question 4   
Les champs utilisés sont nom, prénom, description, fonction.   

Modifier la définition de $Users tel quel :   

`$Users = Import-Csv -Path $CsvFile -Delimiter ";" -Header "prenom","nom","fonction","description" -Encoding UTF8  | Select-Object -Skip 1 ` 

##### Question 5   

Modifier la ligne à la fin du script tel quel :   
`Write-Host "L'utilisateur $Prenom.$Nom avec le mot de passe $Pass a été crée"`  

##### Question 6  

Ajouter une ligne Log avec le PathFile déjà définis plus haut dans $LogFile et ajouter un contenu   
`-Log -PathFile $LogFile -Content "L'utilisateur $Name a été créé"`  

##### Question 7  

Ajouter à la fin du script :  
```
Else {
	Write-Host "L'utilisateur $Name existe deja"
    }  
```

##### Question 8   

Le groupe "Utilisateur" n'existe pas  
Vérifier les groupe avec Get-LocalGroup  
Le groupe "Utilisateurs" au pluriel en revanche existe. Modifier la ligne tel quel :   
`Add-LocalGroupMember -Group "Utilisateurs" -Member "$Name"`  

##### Question 9   

```
    If (-not(Get-LocalUser -Name "$Name"))  
    {  
        $Pass = Random-Password  
        $Password = (ConvertTo-secureString $Pass -AsPlainText -Force)  
        $Description = "$($user.description) - $($User.fonction)"  
        $UserInfo = @{  
            Name                 = "$Nom"  
            FullName             = "$Name"  
	          Description          = $Description  
            Password             = $Password   
            AccountNeverExpires  = $true  
            PasswordNeverExpires = $false  
        }  

        New-LocalUser @UserInfo  
        Add-LocalGroupMember -Group "Utilisateur" -Member "$Name"  
        Write-Host "L'utilisateur $Name avec le mot de passe $Pass a été crée"  
	Log -FilePath $LogFile -Content "L'utilisateur $Name a été créé"  
```

##### Question 10   

Modifier la ligne tel quel :  
`PasswordNeverExpires = $true`  

##### Question 11 

Modifier la ligne première de la fonction mdp tel quel :  
`Function Random-Password ($length = 10)
