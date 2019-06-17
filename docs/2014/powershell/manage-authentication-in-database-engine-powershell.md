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
ms.openlocfilehash: 0992e3a956a2b498d92186fa91c0ed4fbddf6102
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62762045"
---
# <a name="manage-authentication-in-database-engine-powershell"></a>Verwalten der Authentifizierung in PowerShell der Datenbank-Engine
  Standardmäßig wird von den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell-Komponenten beim Herstellen einer Verbindung mit einer [!INCLUDE[ssDE](../includes/ssde-md.md)]-Instanz die Windows-Authentifizierung verwendet. Sie können die SQL Server-Authentifizierung verwenden, indem Sie entweder ein virtuelles PowerShell-Laufwerk definieren oder für `-Username` die Parameter `-Password` und `Invoke-Sqlcmd` angeben.  
  
1.  **Vorbereitungen:**  [Berechtigungen](#Permissions)  
  
2.  **Festlegen der Authentifizierung mit:**  [Ein virtuelles Laufwerk](#SQLAuthVirtDrv), [Invoke-Sqlcmd](#SQLAuthInvSqlCmd)  
  
##  <a name="Permissions"></a> Berechtigungen  
 Alle Aktionen, die Sie in einer [!INCLUDE[ssDE](../includes/ssde-md.md)] -Instanz ausführen können, werden über die Berechtigungen gesteuert, die den beim Verbinden mit der Instanz verwendeten Authentifizierungsinformationen erteilt wurden. Der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anbieter und Cmdlets verwenden standardmäßig das Windows-Konto, unter dem sie ausgeführt werden, um eine Windows-Authentifizierungsverbindung mit [!INCLUDE[ssDE](../includes/ssde-md.md)]herzustellen.  
  
 Zum Herstellen einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierungsverbindung müssen Sie eine Anmelde-ID und ein Kennwort für die SQL Server-Authentifizierung angeben. Bei Verwendung der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anbieter, die Sie zuordnen müssen die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Anmeldeinformationen mit einem virtuellen Laufwerk, und klicken Sie dann mithilfe des Befehls zum Ändern (`cd`) eine Verbindung zu diesem Laufwerk herstellen. In Windows PowerShell können Sicherheitsanmeldeinformationen nur virtuellen Laufwerken zugeordnet werden.  
  
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
  
 Sie werden von der Funktion **sqldrive** zur Eingabe des Kennworts für Ihren Anmeldenamen aufgefordert. Das Kennwort wird bei der Eingabe maskiert. Klicken Sie dann, wenn Sie den Befehl zum Ändern von Verzeichnis verwenden (`cd`) zur Verbindung mit eines Pfads mit den Namen des virtuellen Laufwerks alle Vorgänge ausgeführt werden, mithilfe der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentifizierung-Anmeldeinformationen, die Sie beim Erstellen des Laufwerks angegeben haben.  
  
```  
## Create a function that specifies the login and prompts for the password.  
  
function sqldrive  
{  
    param( [string]$name, [string]$login = "MyLogin", [string]$root = "SQLSERVER:\SQL\MyComputer\MyInstance" )  
    $pwd = read-host -AsSecureString -Prompt "Password"  
    $cred = new-object System.Management.Automation.PSCredential -argumentlist $login,$pwd  
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
  
```  
## Prompt the user for their password.  
$pwd = read-host -AsSecureString -Prompt "Password"  
  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance" -Username "MyLogin" -Password $pwd  
```  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-PowerShell](sql-server-powershell.md)   
 [SQL Server PowerShell-Anbieter](sql-server-powershell-provider.md)   
 [Invoke-Sqlcmd-Cmdlet](../database-engine/invoke-sqlcmd-cmdlet.md)  
  
  
