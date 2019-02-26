---
title: SQL Server-Anmeldedialogfeld (OLE DB) | Microsoft-Dokumentation
description: Dialogfeld „SQL Server-Anmeldung“ (ODBC)
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
ms.author: v-beaziz
author: bazizi
ms.openlocfilehash: 4735ead33dc7c3a6d633e3b23ff1da97eeae4962
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744832"
---
# <a name="sql-server-login-dialog-box"></a>SQL Server-Anmeldedialogfeld
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Wenn Sie versuchen, eine Verbindung herstellen, ohne ausreichende Informationen anzugeben, zeigt der OLE DB-Treiber die **SQL Server-Anmeldung** Dialogfeld.

> [!NOTE]  
> SQL Server-Anmeldedialogfeld Aufforderung Verhalten wird gesteuert, indem die `DBPROP_INIT_PROMPT` -Eigenschaft zur datenquelleninitialisierung. Weitere Informationen finden Sie in den folgenden Themen:
> - [Initialisierungs- und Autorisierungseigenschaften](../ole-db-data-source-objects/initialization-and-authorization-properties.md)
> - [OLE DB Programmer's Guide](https://go.microsoft.com/fwlink/?linkid=2067702)

![Screenshot des Dialogfelds für SQL Server-Anmeldung](../media/sql-server-login-dialog.png)

## <a name="options"></a>enthalten
|Option|und Beschreibung|
|---   |---        |
|Server|Der Name einer Instanz von SQL Server in Ihrem Netzwerk. Wählen Sie einen Server-/Instanzennamen aus der Liste aus, oder geben Sie den Server-/Instanzennamen in das Feld **Server** ein. Optional können Sie mit dem **SQL Server-Konfigurations-Manager** einen Serveralias auf dem Clientcomputer erstellen und diesen Namen in das Feld **Server** eingeben. <br/><br/>Sie können „(local)“ eingeben, wenn Sie den gleichen Computer wie SQL Server verwenden. Sie können anschließend eine Verbindung mit einer lokalen Instanz von SQL Server herstellen, selbst wenn eine nicht vernetzte Version von SQL Server ausgeführt wird.<br/><br/>Weitere Informationen über Servernamen für verschiedene Typen von Netzwerken finden Sie unter [SQL Server-Installation](https://go.microsoft.com/fwlink/?linkid=2067541).|
|Authentifizierungsmodus|Sie können die folgenden Authentifizierungsoptionen aus der Dropdown-Liste auswählen:<br/><ul><li>`Windows Authentication:` SQL Server mit den Anmeldeinformationen des aktuell angemeldeten Benutzers Windows-Authentifizierung.</li><li>`SQL Server Authentication:` Authentifizierung mit SQL Server mithilfe der Anmelde-ID und Kennwort.</li><li>`Active Directory - Integrated:` Integrierte Authentifizierung mit Windows den Anmeldeinformationen des aktuell angemeldeten Benutzers.</li><li>`Active Directory - Password:` Active Directory-Authentifizierung mit Anmelde-ID und Kennwort.</li></ul>|
|Server-SPN|Wenn Sie eine vertrauenswürdige Verbindung verwenden, können Sie einen Dienstprinzipalnamen (SPN) für den Server angeben.|
|Login ID|Gibt die Anmelde-ID, die für die Verbindung verwendet. Im Textfeld "Anmelde-ID" ist nur aktiviert, wenn `Authentication Mode` nastaven NA hodnotu `SQL Server Authentication` oder `Active Directory - Password`.|
|Kennwort|Gibt das Kennwort für die Verbindung verwendet. Das Kennwort-Textfeld ist nur aktiviert, wenn `Authentication Mode` nastaven NA hodnotu `SQL Server Authentication` oder `Active Directory - Password`.|
|enthalten|Zeigt die Gruppe **Optionen** an oder blendet sie aus. Die Schaltfläche **Optionen** wird aktiviert, wenn **Server** über einen Wert verfügt.|
|Ändern des Kennworts|Wenn dieses Kontrollkästchen aktiviert, können **neues Kennwort** und **neues Kennwort bestätigen** Textfelder.|
|Neues Kennwort|Gibt das neue Kennwort an.|
|Neues Kennwort bestätigen|Gibt das neue Kennwort zur Bestätigung ein zweites Mal an.|
|Datenbank|Gibt die Standarddatenbank an, die für die Verbindung verwendet werden soll. Diese Einstellung überschreibt die für die Anmeldung auf dem Server festgelegte Standarddatenbank. Wenn keine Datenbank angegeben ist, wird für die Verbindung die Standarddatenbank verwendet, die für die Anmeldung auf dem Server angegeben ist.|
|Spiegelserver|Gibt den Namen des Failoverpartners der zu spiegelnden Datenbank an.|
|Spiegelserver-SPN|Optional können Sie einen SPN für den Spiegelserver angeben. Der SPN für den Spiegelserver wird zur gegenseitigen Authentifizierung zwischen Client und Server verwendet.|
|Sprache|Gibt die Landessprache an, die für SQL Server-Systemmeldungen verwendet werden soll. Auf dem Computer, auf dem SQL Server ausgeführt wird, muss dies Sprache installiert sein. Diese Einstellung überschreibt die für die Anmeldung auf dem Server festgelegte Standardsprache. Wenn keine Sprache angegeben ist, wird für die Verbindung die Standardsprache verwendet, die für die Anmeldung auf dem Server angegeben ist.|
|ApplicationName|(Optional) Gibt den Anwendungsnamen an, der in der Spalte **program_name** in der Zeile für diese Verbindung in **sys.sysprocesses** gespeichert werden soll.|
|Workstation ID|(Optional) Gibt die Workstation ID an, die in der Spalte **hostname** in der Zeile für diese Verbindung in **sys.sysprocesses** gespeichert werden soll.|
|Starke Verschlüsselung für Daten verwenden|Wenn diese Option aktiviert ist, werden Daten, die über die Verbindung übergeben wird verschlüsselt.|
|Serverzertifikat vertrauen|Wenn diese Option aktiviert ist, wird das Zertifikat des Servers überprüft werden. Zertifikat des Servers muss der richtige Hostname des Servers und von einer vertrauenswürdigen Zertifizierungsstelle ausgestellt.|

> [!NOTE]  
> Bei Verwendung `Windows Authentication` oder `SQL Server Authentication` Modi **Serverzertifikat vertrauen** gilt nur, wenn die **starke Verschlüsselung für Daten verwenden** aktiviert ist.

## <a name="next-steps"></a>Nächste Schritte
- [Authentifizieren Sie sich bei Azure Active Directory](../features/using-azure-active-directory.md) mit dem OLE DB-Treiber.
- Mithilfe von Set Verbindung Informationen [Universal Data Link (UDL)](data-link-pages.md).