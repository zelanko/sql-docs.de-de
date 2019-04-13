---
title: Arbeiten mit dem WMI-Anbieter für die Konfigurationsverwaltung | Microsoft-Dokumentation
ms.custom: ''
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
manager: craigg
ms.openlocfilehash: 20a34f01908333650a4c5b566ccab2221a4e07c2
ms.sourcegitcommit: acb5de9f493238180d13baa302552fdcc30d83c0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59542120"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a>Arbeiten mit dem WMI-Anbieter für die Konfigurationsverwaltung

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Dieser Artikel enthält Informationen zum Programm mit dem WMI-Anbieter für die Computerverwaltung.

## <a name="binding"></a>Bindung  
 Der WMI-Anbieter für die Konfigurationsverwaltung ist ein COM-Objektmodell und unterstützt frühes und spätes Binden. Mit spätem Binden können Sie Skriptsprachen wie VBScript verwenden, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste, Netzwerkeinstellungen und Aliasnamen programmgesteuert zu bearbeiten.  
  
## <a name="specifying-a-connection-string"></a>Angeben einer Verbindungszeichenfolge

Anwendungen leiten den WMI-Anbieter für die Konfigurationsverwaltung an eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] weiter, indem sie eine Verbindung zu einem vom Anbieter definierten WMI-Namespace herstellen. Der Windows-WMI-Dienst ordnet diesen Namespace auf die DLL des Anbieters, und die DLL in den Arbeitsspeicher geladen. Alle Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden mit einem einzigen WMI-Namespace dargestellt.

Der Namespace standardmäßig im folgenden Format verwendet. Im Format `VV` ist die Anzahl der Hauptversion von SQL Server. Die Anzahl ist mit sichtbaren `SELECT @@VERSION;`.

```console
\\.\root\Microsoft\SqlServer\ComputerManagementVV
```

Wenn Sie die Verbindung mithilfe von PowerShell das führende `\\.\` müssen entfernt werden. Beispielsweise führt die folgende PowerShell-Code alle WMI-Klassen für eine SQL Server 2016, d.h. Hauptversion 13.

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

Sie können folgende PowerShell-Code verwenden, um alle verfügbaren ComputerManagement von WMI-Namespaces zu Abfragen.

```powershell
gwmi -ns 'root\Microsoft\SqlServer' __NAMESPACE | ? {$_.name -match 'ComputerManagement' } | select name
```

 **Hinweis**: Wenn Sie über Windows-Firewall herstellen müssen Sie sicherstellen, dass Ihr Computer geeignet konfiguriert sind. Finden Sie im Artikel "Connecting Through Windows Firewall" in der Dokumentation zu Windows-Verwaltungsinstrumentation [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [Website](https://go.microsoft.com/fwlink/?linkid=15426).  
  
## <a name="permissions-and-server-authentication"></a>Berechtigungen und Serverauthentifizierung  
 Für den Zugriff auf den WMI-Anbieter für die Konfigurationsverwaltung muss das WMI-Verwaltungsskript des Clients im Kontext eines Administrators auf dem Zielcomputer ausgeführt werden. Sie müssen ein Mitglied der lokalen Windows-Administratorengruppe auf dem Computer sein, den Sie verwalten möchten.  
  
 Der Administrator kann Gruppenrichtlinien festlegen, um den Benutzerzugriff auf WMI-Anbieter zu kontrollieren. Weitere Informationen zum Festlegen von Gruppenrichtlinien finden Sie im Abschnitt zu Gruppenrichtlinien und MMC in der Hilfe zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager.  
  
 Das WMI-Verwaltungsskript kann zum Aktualisieren des Kontos verwendet werden, unter dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste ausgeführt werden.  
  
 Sicherheitszertifikate werden vom WMI-Anbieter für die Konfigurationsverwaltung unterstützt. Weitere Informationen zu Zertifikaten finden Sie unter [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Konfigurations-Manager](../../relational-databases/sql-server-configuration-manager.md)  
  
  
