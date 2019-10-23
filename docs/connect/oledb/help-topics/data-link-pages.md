---
title: Konfiguration von Universal Data Link (UDL) | Microsoft-Dokumentation
description: Universal Data Link (UDL)-Konfiguration mit Microsoft OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
ms.author: v-beaziz
author: bazizi
ms.openlocfilehash: d92555fba1d9e0a380ffdc9051817ddfae9ca4b7
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381757"
---
# <a name="universal-data-link-udl-configuration"></a>Universal Data Link (UDL)-Konfiguration
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

## <a name="connection-tab"></a>Registerkarte Verbindung
Geben Sie auf der Registerkarte Verbindung an, wie Sie mithilfe des Microsoft OLE DB-Treibers für SQL Server eine Verbindung mit Ihren Daten herstellen.

![Screenshot der OLE DB Daten Link Seiten-Registerkarte "Verbindung"](../media/data-link-pages-connection-tab.png)

Diese Registerkarte „Verbindung“ ist anbieterspezifisch und zeigt nur die Verbindungseigenschaften an, die für den Microsoft OLE DB-Treiber für SQL Server erforderlich sind.

|Option|und Beschreibung|
|---   |---        |
|Wählen Sie einen Servernamen aus, oder geben Sie ihn ein.|Wählen Sie den Namen eines Servers aus der Dropdownliste, oder geben Sie den Speicherort des Servers ein, auf dem sich die gewünschte Datenbank befindet. Das Auswählen der Datenbank auf dem Server ist eine separate Aktion. Aktualisieren Sie die Liste, indem Sie auf „Aktualisieren“ klicken.
|Geben Sie die Informationen ein, um sich beim Server anzumelden.|In dieser Dropdown Liste können Sie die folgenden Authentifizierungs Optionen auswählen: <ul><li>`Windows Authentication:` Authentifizierung zum SQL Server mithilfe der Anmelde Informationen für das Windows-Konto des aktuell angemeldeten Benutzers.</li><li>`SQL Server Authentication:` Authentifizierung mit Anmelde-ID und Kennwort.</li><li>`Active Directory - Integrated:` integrierte Authentifizierung mit einer Azure Active Directory-Identität. Dieser Modus kann auch zur SQL Server der Windows-Authentifizierung verwendet werden.</li><li>`Active Directory - Password:` Benutzer-ID-und Kenn Wort Authentifizierung mit einer Azure Active Directory-Identität.</li><li>`Active Directory - Universal with MFA support:` interaktive Authentifizierung mit einer Azure Active Directory-Identität. Dieser Modus unterstützt Azure Multi-Factor Authentication (MFA).</li></ul>|
|Server-SPN|Wenn Sie eine vertrauenswürdige Verbindung verwenden, können Sie einen Dienstprinzipalnamen (SPN) für den Server angeben.|
|Benutzername|Geben Sie die Benutzer-ID ein, die bei der Anmeldung bei der Datenquelle für die Authentifizierung verwendet werden soll.|
|Kennwort|Geben Sie das Kennwort ein, das bei der Anmeldung bei der Datenquelle für die Authentifizierung verwendet werden soll.|
|Leeres Kennwort|Wenn diese Option aktiviert ist, kann der angegebene Anbieter in der Verbindungs Zeichenfolge ein leeres Kennwort verwenden.|
|Speichern von Kennwort zulassen|Wenn diese Option aktiviert ist, kann das Kennwort mit der Verbindungs Zeichenfolge gespeichert werden. Es hängt von den Funktionen der aufrufenden Anwendung ab, ob das Kennwort in der Verbindungszeichenfolge enthalten ist. <br/><br/>**HINWEIS:** Das Kennwort wird ohne Maskierung und Verschlüsselung zurückgegeben und gespeichert.|
|Starke Verschlüsselung für Daten verwenden|Wenn diese Option aktiviert ist, werden die Daten, die über die Verbindung übermittelt werden, verschlüsselt.|
|Serverzertifikat vertrauen|Wenn dieses Kontrollkästchen aktiviert ist, wird das Zertifikat des Servers überprüft. Das Serverzertifikat muss über den richtigen Hostnamen des Servers verfügen und von einer vertrauenswürdigen Zertifizierungsstelle ausgestellt werden.|
|Datenbank auswählen|Wählen Sie den gewünschten Datenbanknamen aus, oder geben Sie ihn ein.|
|Datenbankdatei als Datenbankname anfügen|Gibt den Namen der primären Datei für eine anfügbare Datenbank an. Diese Datenbank wird angefügt und als Standarddatenbank für die Datenquelle verwendet. Geben Sie im ersten Textfeld unter diesem Abschnitt den Datenbanknamen ein, der für die angefügte Datenbankdatei verwendet werden soll.<br/><br/>Geben Sie den vollständigen Pfad der Datenbankdatei ein, die in das Textfeld mit der Bezeichnung `Using the filename` angefügt werden soll, oder klicken Sie auf die Schaltfläche `...`, um die Datenbankdatei|
|Ändern des Kennworts|Zeigt das Dialogfeld SQL Server Kennwort ändern an. |
|Verbindung testen|Klicken Sie, um eine Verbindung mit der angegebenen Datenquelle herzustellen. Wenn die Verbindung fehlschlägt, stellen Sie sicher, dass die Einstellungen richtig sind. Zum Beispiel können Rechtschreibfehler und die Unterscheidung nach Groß-/Kleinschreibung das Fehlschlagen von Verbindungen verursachen.|

## <a name="advanced-tab"></a>Registerkarte „Erweitert“
Verwenden Sie die Registerkarte Erweitert, um zusätzliche Initialisierungs Eigenschaften anzuzeigen und festzulegen.

![Screenshot der OLE DB Daten Link Seiten-Registerkarte "Erweitert"](../media/data-link-pages-advanced-tab.png)

|Option|und Beschreibung|
|---   |---        |
| Connect timeout | Gibt die Zeitspanne (in Sekunden) an, die der Microsoft OLE DB-Treiber für SQL Server auf den Abschluss der Initialisierung wartet. Wenn es bei der Initialisierung zu einem Timeout kommt, wird ein Fehler zurückgegeben, und die Verbindung wird nicht hergestellt.|


> [!NOTE]  
>  Weitere allgemeine Informationen zur Verbindungs Herstellung mit Daten finden Sie in der [Übersicht über die Daten Link-API](https://go.microsoft.com/fwlink/?linkid=2067432).

## <a name="next-steps"></a>Nächste Schritte
- [Authentifizieren Sie sich bei Azure Active Directory](../features/using-azure-active-directory.md) mithilfe des OLE DB Treibers.

- [Benutzer zur Authentifizierung von Anmelde](../help-topics/sql-server-login-dialog.md) Informationen mithilfe des OLE DB Treibers auffordern.