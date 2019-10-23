---
title: Dialog Feld "SQL Server Anmeldung" (OLE DB) | Microsoft-Dokumentation
description: Verwenden des Dialogfelds „SQL Server-Anmeldung“
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
ms.author: v-beaziz
author: bazizi
ms.openlocfilehash: d35c339798b4385cb903d8a4a83f13184bbf4db3
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381748"
---
# <a name="sql-server-login-dialog-box"></a>Dialogfeld „SQL Server-Anmeldung“
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Wenn Sie versuchen, eine Verbindung herzustellen, ohne ausreichend Informationen anzugeben, zeigt der OLE DB Treiber das **SQL Server Anmelde** Dialogfeld an.

> [!NOTE]  
> SQL Server Anmelde Dialogfeld, das das Verhalten anfordert, wird von der `DBPROP_INIT_PROMPT` Initialisierungs Eigenschaft gesteuert Weitere Informationen finden Sie in den folgenden Themen:
> - [Initialisierungs- und Autorisierungseigenschaften](../ole-db-data-source-objects/initialization-and-authorization-properties.md)
> - [Programmiererhandbuch für OLE DB](https://go.microsoft.com/fwlink/?linkid=2067702)

![Screenshot des Dialog Felds "SQL Server Anmeldung"](../media/sql-server-login-dialog.png)

## <a name="options"></a>enthalten
|Option|und Beschreibung|
|---   |---        |
|Server|Der Name einer Instanz von SQL Server in Ihrem Netzwerk. Wählen Sie einen Server-/Instanzennamen aus der Liste aus, oder geben Sie den Server-/Instanzennamen in das Feld **Server** ein. Optional können Sie mit dem **SQL Server-Konfigurations-Manager** einen Serveralias auf dem Clientcomputer erstellen und diesen Namen in das Feld **Server** eingeben. <br/><br/>Sie können „(local)“ eingeben, wenn Sie den gleichen Computer wie SQL Server verwenden. Sie können anschließend eine Verbindung mit einer lokalen Instanz von SQL Server herstellen, selbst wenn eine nicht vernetzte Version von SQL Server ausgeführt wird.<br/><br/>Weitere Informationen zu Servernamen für verschiedene Typen von Netzwerken finden Sie unter [SQL Server Installation](https://go.microsoft.com/fwlink/?linkid=2067541).|
|Authentifizierungsmodus|Sie können die folgenden Authentifizierungs Optionen aus der Dropdown Liste auswählen:<br/><ul><li>`Windows Authentication:` Authentifizierung zum SQL Server mithilfe der Anmelde Informationen für das Windows-Konto des aktuell angemeldeten Benutzers.</li><li>`SQL Server Authentication:` Authentifizierung mit Anmelde-ID und Kennwort.</li><li>`Active Directory - Integrated:` integrierte Authentifizierung mit einer Azure Active Directory-Identität. Dieser Modus kann auch zur SQL Server der Windows-Authentifizierung verwendet werden.</li><li>`Active Directory - Password:` Benutzer-ID-und Kenn Wort Authentifizierung mit einer Azure Active Directory-Identität.</li><li>`Active Directory - Universal with MFA support:` interaktive Authentifizierung mit einer Azure Active Directory-Identität. Dieser Modus unterstützt Azure Multi-Factor Authentication (MFA).</li></ul>|
|Server-SPN|Wenn Sie eine vertrauenswürdige Verbindung verwenden, können Sie einen Dienstprinzipalnamen (SPN) für den Server angeben.|
|Login ID|Gibt die Anmelde-ID an, die für die Verbindung verwendet werden soll. Das Textfeld Anmelde-ID ist nur aktiviert, wenn `Authentication Mode` auf `SQL Server Authentication`, `Active Directory - Password` oder `Active Directory - Universal with MFA support` festgelegt ist.|
|Kennwort|Gibt das für die Verbindung verwendete Kennwort an. Das Textfeld Kennwort ist nur aktiviert, wenn `Authentication Mode` auf `SQL Server Authentication` oder `Active Directory - Password` festgelegt ist.|
|enthalten|Zeigt die Gruppe **Optionen** an oder blendet sie aus. Die Schaltfläche **Optionen** wird aktiviert, wenn **Server** über einen Wert verfügt.|
|Ändern des Kennworts|Wenn diese Option aktiviert ist, werden die Textfelder **Neues Kennwort** und **Kennwort bestätigen** aktiviert.|
|Neues Kennwort|Gibt das neue Kennwort an.|
|Neues Kennwort bestätigen|Gibt das neue Kennwort zur Bestätigung ein zweites Mal an.|
|Datenbank|Wählen Sie die Standarddatenbank aus, die für die Verbindung verwendet werden soll, oder geben Sie sie ein. Diese Einstellung überschreibt die für die Anmeldung auf dem Server festgelegte Standarddatenbank. Wenn keine Datenbank angegeben ist, wird für die Verbindung die Standarddatenbank verwendet, die für die Anmeldung auf dem Server angegeben ist.|
|Spiegelserver|Gibt den Namen des Failoverpartners der zu spiegelnden Datenbank an.|
|Spiegelserver-SPN|Optional können Sie einen SPN für den Spiegelserver angeben. Der SPN für den Spiegelserver wird zur gegenseitigen Authentifizierung zwischen Client und Server verwendet.|
|Sprache|Gibt die Landessprache an, die für SQL Server-Systemmeldungen verwendet werden soll. Auf dem Computer, auf dem SQL Server ausgeführt wird, muss dies Sprache installiert sein. Diese Einstellung überschreibt die für die Anmeldung auf dem Server festgelegte Standardsprache. Wenn keine Sprache angegeben ist, wird für die Verbindung die Standardsprache verwendet, die für die Anmeldung auf dem Server angegeben ist.|
|ApplicationName|Gibt den Anwendungsnamen an, der in der Spalte **program_name** in der Zeile für diese Verbindung in **sys.sysprocesses** gespeichert werden soll.|
|Workstation ID|Gibt die Arbeitsstations-ID an, die in der Spalte **hostname** in der Zeile für diese Verbindung in **sys.sysprocesses** gespeichert werden soll.|
|Starke Verschlüsselung für Daten verwenden|Wenn diese Option aktiviert ist, werden die Daten, die über die Verbindung übermittelt werden, verschlüsselt.|
|Serverzertifikat vertrauen|Wenn dieses Kontrollkästchen aktiviert ist, wird das Zertifikat des Servers überprüft. Das Serverzertifikat muss über den richtigen Hostnamen des Servers verfügen und von einer vertrauenswürdigen Zertifizierungsstelle ausgestellt werden.|

> [!NOTE]  
> Wenn Sie `Windows Authentication`-oder `SQL Server Authentication` Modi verwenden, wird das **Serverzertifikat vertrauen** nur dann berücksichtigt, wenn die Option **starke Verschlüsselung für Daten verwenden** aktiviert ist.

## <a name="next-steps"></a>Nächste Schritte
- [Authentifizieren Sie sich bei Azure Active Directory](../features/using-azure-active-directory.md) mithilfe des OLE DB Treibers.
- Legen Sie Verbindungsinformationen mithilfe [Universal Data Link (UDL)](data-link-pages.md)fest.