---
title: Verwenden des WMI-Anbieters für die Konfigurations Verwaltung
ms.custom: seo-lt-2019
ms.date: 04/12/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- permissions [WMI]
- connection strings [WMI]
- security [WMI]
- WMI Provider for Configuration Management, connection strings
- WMI Provider for Configuration Management, security
- late binding [WMI]
- WMI Provider for Configuration Management, late binding
- binding [WMI]
ms.assetid: 34daa922-7074-41d0-9077-042bb18c222a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d76cc006e2f8638de9b6d3c21660806239022ec0
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73657374"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a>Arbeiten mit dem WMI-Anbieter für die Konfigurationsverwaltung

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Dieser Artikel enthält Anleitungen zum Programmieren mit dem WMI-Anbieter für die Computer Verwaltung.

## <a name="binding"></a>Bindung  
 Der WMI-Anbieter für die Konfigurationsverwaltung ist ein COM-Objektmodell und unterstützt frühes und spätes Binden. Mit spätem Binden können Sie Skriptsprachen wie VBScript verwenden, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste, Netzwerkeinstellungen und Aliasnamen programmgesteuert zu bearbeiten.  
  
## <a name="specifying-a-connection-string"></a>Angeben einer Verbindungszeichenfolge

Anwendungen leiten den WMI-Anbieter für die Konfigurationsverwaltung an eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] weiter, indem sie eine Verbindung zu einem vom Anbieter definierten WMI-Namespace herstellen. Der Windows WMI-Dienst ordnet diesen Namespace der Anbieter-DLL zu und lädt die dll in den Arbeitsspeicher. Alle Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden mit einem einzigen WMI-Namespace dargestellt.

Der Namespace weist standardmäßig das folgende Format auf. Im Format ist `VV` die Hauptversionsnummer von SQL Server. Die Zahl kann durch Ausführen von `SELECT @@VERSION;`erkannt werden.

```console
\\.\root\Microsoft\SqlServer\ComputerManagementVV
```

Wenn Sie mithilfe von PowerShell eine Verbindung herstellen, müssen die führenden `\\.\` entfernt werden. Der folgende PowerShell-Code listet z. b. alle WMI-Klassen für eine SQL Server 2016 auf, bei der es sich um die Hauptversion 13 handelt.

```powershell
Get-WmiObject -Namespace 'root\Microsoft\SqlServer\ComputerManagement13' -List
```

<!--
Updated this on 2019-04-12, per:
   ~ https://github.com/MicrosoftDocs/sql-docs/issues/1817
   ~ https://github.com/rrg92/sql-docs/commit/3d518bfc0d55f819c762abc3e5c5c9eed85abe94?diff=unified

Thus from here I (GeneMi = MightyPen) removed the following text about 'instance_name':

'root\Microsoft\SqlServer\ComputerManagement13\instance_name'

where `instance_name` defaults to `MSSQLSERVER` in a default installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
-->

Sie können den folgenden PowerShell-Code verwenden, um alle verfügbaren WMI-Computerverwaltungs-Namespaces abzufragen.

```powershell
gwmi -ns 'root\Microsoft\SqlServer' __NAMESPACE | ? {$_.name -match 'ComputerManagement' } | select name
```

 **Hinweis:** Wenn Sie über die Windows-Firewall eine Verbindung herstellen, müssen Sie sicherstellen, dass Ihre Computer ordnungsgemäß konfiguriert sind. Weitere Informationen finden Sie im Artikel "Herstellen einer Verbindung über die Windows-Firewall" in der Windows-Verwaltungsinstrumentation Dokumentation auf [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN- [Website](https://go.microsoft.com/fwlink/?linkid=15426).  
  
## <a name="permissions-and-server-authentication"></a>Berechtigungen und Serverauthentifizierung  
 Für den Zugriff auf den WMI-Anbieter für die Konfigurationsverwaltung muss das WMI-Verwaltungsskript des Clients im Kontext eines Administrators auf dem Zielcomputer ausgeführt werden. Sie müssen ein Mitglied der lokalen Windows-Administratorengruppe auf dem Computer sein, den Sie verwalten möchten.  
  
 Der Administrator kann Gruppenrichtlinien festlegen, um den Benutzerzugriff auf WMI-Anbieter zu kontrollieren. Weitere Informationen zum Festlegen von Gruppenrichtlinien finden Sie im Abschnitt zu Gruppenrichtlinien und MMC in der Hilfe zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager.  
  
 Das WMI-Verwaltungsskript kann zum Aktualisieren des Kontos verwendet werden, unter dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste ausgeführt werden.  
  
 Sicherheitszertifikate werden vom WMI-Anbieter für die Konfigurationsverwaltung unterstützt. Weitere Informationen zu Zertifikaten finden Sie in der [Verschlüsselungs Hierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Konfigurations-Manager](../../relational-databases/sql-server-configuration-manager.md)  
  
  
