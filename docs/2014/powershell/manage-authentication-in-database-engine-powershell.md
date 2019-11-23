---
title: Verwalten der Authentifizierung in PowerShell der Datenbank-Engine | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: ab9212a6-6628-4f08-a38c-d3156e05ddea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4a04e581758748d55b9defcab3beaa6a86f0eecf
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72797797"
---
# <a name="manage-authentication-in-database-engine-powershell"></a>Verwalten der Authentifizierung in PowerShell der Datenbank-Engine
  Standardmäßig wird von den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell-Komponenten beim Herstellen einer Verbindung mit einer [!INCLUDE[ssDE](../includes/ssde-md.md)]-Instanz die Windows-Authentifizierung verwendet. Sie können die SQL Server-Authentifizierung verwenden, indem Sie entweder ein virtuelles PowerShell-Laufwerk definieren oder für `-Username` die Parameter `-Password` und `Invoke-Sqlcmd` angeben.  
  
1.  **Before you begin:**  [Permissions](#Permissions)  
  
2.  **Festlegen der Authentifizierung mit:**  [einem virtuellen Laufwerk](#SQLAuthVirtDrv), [Invoke-Sqlcmd](#SQLAuthInvSqlCmd)  
  
##  <a name="Permissions"></a> Berechtigungen  
 Alle Aktionen, die Sie in einer [!INCLUDE[ssDE](../includes/ssde-md.md)] -Instanz ausführen können, werden über die Berechtigungen gesteuert, die den beim Verbinden mit der Instanz verwendeten Authentifizierungsinformationen erteilt wurden. Der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anbieter und Cmdlets verwenden standardmäßig das Windows-Konto, unter dem sie ausgeführt werden, um eine Windows-Authentifizierungsverbindung mit [!INCLUDE[ssDE](../includes/ssde-md.md)]herzustellen.  
  
 Zum Herstellen einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierungsverbindung müssen Sie eine Anmelde-ID und ein Kennwort für die SQL Server-Authentifizierung angeben. Wenn Sie den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Anbieter verwenden, müssen Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Anmelde Informationen einem virtuellen Laufwerk zuordnen und dann den Befehl "Verzeichnis wechseln" (`cd`) verwenden, um eine Verbindung mit diesem Laufwerk herzustellen. In Windows PowerShell können Sicherheitsanmeldeinformationen nur virtuellen Laufwerken zugeordnet werden.  
  
##  <a name="SQLAuthVirtDrv"></a> SQL Server-Authentifizierung mit einem virtuellen Laufwerk  
 **So erstellen Sie ein virtuelles Laufwerk mit Zuordnung zu einer SQL Server-Authentifizierungsanmeldung**  
  
1.  Erstellen Sie eine Funktion, auf die Folgendes zutrifft:  
  
    1.  Sie verfügt über Parameter für den Namen, der dem virtuellen Laufwerk zugeordnet werden soll, für die Anmelde-ID und für den Anbieterpfad, der dem virtuellen Laufwerk zugeordnet werden soll.  
  
    2.  Sie verwendet `read-host`, um den Benutzer zur Eingabe des Kennworts aufzufordern.  
  
    3.  Sie verwendet `new-object`, um ein Anmeldeinformationenobjekt zu erstellen.  
  
    4.  Sie verwendet `new-psdrive`, um ein virtuelles Laufwerk mit den angegebenen Anmeldeinformationen zu erstellen.  
  
2.  Rufen Sie die Funktion auf, um ein virtuelles Laufwerk mit den angegebenen Anmeldeinformationen zu erstellen.  
  
### <a name="example-virtual-drive"></a>Beispiel (virtuelles Laufwerk)  
 In diesem Beispiel wird eine Funktion mit dem Namen **sqldrive** erstellt, mit der Sie ein virtuelles Laufwerk erstellen können, das mit dem angegebenen Anmeldenamen für die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung und der angegebenen Instanz verknüpft ist.  
  
 Sie werden von der Funktion **sqldrive** zur Eingabe des Kennworts für Ihren Anmeldenamen aufgefordert. Das Kennwort wird bei der Eingabe maskiert. Wenn Sie dann den Befehl "Verzeichnis wechseln" (`cd`) verwenden, um mithilfe des Namens des virtuellen Laufwerks eine Verbindung mit einem Pfad herzustellen, werden alle Vorgänge mithilfe der Anmelde Informationen für die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Authentifizierung ausgeführt, die Sie beim Erstellen des Laufwerks angegeben haben.  
  
```powershell
## Create a function that specifies the login and prompts for the password.  
  
function sqldrive  
{  
    param( [string]$name, [string]$login = "MyLogin", [string]$root = "SQLSERVER:\SQL\MyComputer\MyInstance" )  
    $pwd = Read-Host -AsSecureString -Prompt "Password"  
    $cred = New-Object System.Management.Automation.PSCredential -argumentlist $login, $pwd  
    New-PSDrive $name -PSProvider SqlServer -Root $root -Credential $cred -Scope 1  
}  
  
## Use the sqldrive function to create a SQLAuth virtual drive.  
sqldrive SQLAuth  
  
## CD to the virtual drive, which invokes the supplied authentication credentials.  
cd SQLAuth  
```  
  
##  <a name="SQLAuthInvSqlCmd"></a> SQL Server-Authentifizierung mit Invoke-Sqlcmd  
 **So verwenden Sie Invoke-Sqlcmd mit der SQL Server-Authentifizierung**  
  
1.  Verwenden Sie den `-Username`-Parameter, um eine Anmelde-ID anzugeben, und den `-Password`-Parameter, um das zugeordnete Kennwort anzugeben.  
  
### <a name="example-invoke-sqlcmd"></a>Beispiel (Invoke-Sqlcmd)  
 In diesem Beispiel wird das "read-host"-Cmdlet verwendet, um den Benutzer zur Eingabe des Kennworts aufzufordern, und dann unter Verwendung der SQL Server-Authentifizierung eine Verbindung hergestellt.  
  
```powershell
## Prompt the user for their password.  
$pwd = Read-Host -AsSecureString -Prompt "Password"  
  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance" -Username "MyLogin" -Password $pwd  
```  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server PowerShell](sql-server-powershell.md)   
 [SQL Server PowerShell-Anbieter](sql-server-powershell-provider.md)   
 [Invoke-Sqlcmd-Cmdlet](../database-engine/invoke-sqlcmd-cmdlet.md)  
