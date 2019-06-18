---
title: Universal Data Link (UDL) Configuration | Microsoft-Dokumentation
description: Universal Data Link (UDL)-Konfiguration mithilfe von Microsoft OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
ms.author: v-beaziz
author: bazizi
ms.openlocfilehash: e198f561fd4f6bcec390ef8632c1cdc96f2810d6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62854675"
---
# <a name="universal-data-link-udl-configuration"></a>Universal Data Link (UDL)-Konfiguration
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

## <a name="connection-tab"></a>Registerkarte "Verbindung"
Verwenden Sie die Registerkarte "Verbindung" zum Herstellen einer Verbindung mit Ihren Daten mithilfe der Microsoft OLE DB-Treiber für SQL Server angeben.

![Screenshot des OLE DB Data Link-Seiten – Registerkarte "Verbindung"](../media/data-link-pages-connection-tab.png)

Diese Registerkarte „Verbindung“ ist anbieterspezifisch und zeigt nur die Verbindungseigenschaften an, die für den Microsoft OLE DB-Treiber für SQL Server erforderlich sind.

|Option|und Beschreibung|
|---   |---        |
|Wählen Sie einen Servernamen aus, oder geben Sie ihn ein.|Wählen Sie den Namen eines Servers aus der Dropdownliste, oder geben Sie den Speicherort des Servers ein, auf dem sich die gewünschte Datenbank befindet. Das Auswählen der Datenbank auf dem Server ist eine separate Aktion. Aktualisieren Sie die Liste, indem Sie auf „Aktualisieren“ klicken.
|Geben Sie Informationen zum Anmelden an den server|Sie können die folgenden Authentifizierungsoptionen aus der Dropdown-Liste auswählen: <ul><li>`Windows Authentication:` SQL Server mit den Anmeldeinformationen des aktuell angemeldeten Benutzers Windows-Authentifizierung.</li><li>`SQL Server Authentication:` Authentifizierung mit SQL Server mithilfe der Anmelde-ID und Kennwort.</li><li>`Active Directory - Integrated:` Integrierte Authentifizierung mit Windows den Anmeldeinformationen des aktuell angemeldeten Benutzers.</li><li>`Active Directory - Password:` Active Directory-Authentifizierung mit Anmelde-ID und Kennwort.</li></ul>|
|Server-SPN|Wenn Sie eine vertrauenswürdige Verbindung verwenden, können Sie einen Dienstprinzipalnamen (SPN) für den Server angeben.|
|Benutzername|Geben Sie die Benutzer-ID zur Authentifizierung verwendet werden soll, wenn Sie mit der Datenquelle anmelden.|
|Kennwort|Geben Sie das Kennwort zur Authentifizierung verwendet werden soll, wenn Sie mit der Datenquelle anmelden.|
|Leeres Kennwort|Wenn diese Option aktiviert ist, können den angegebenen Anbieter auf ein leeres Kennwort in der Verbindungszeichenfolge zu verwenden.|
|Speichern von Kennwort zulassen|Wenn diese Option aktiviert ist, können das Kennwort an, mit der Verbindungszeichenfolge gespeichert werden. Es hängt von den Funktionen der aufrufenden Anwendung ab, ob das Kennwort in der Verbindungszeichenfolge enthalten ist. <br/><br/>**HINWEIS:** Das Kennwort wird ohne Maskierung und Verschlüsselung zurückgegeben und gespeichert.|
|Starke Verschlüsselung für Daten verwenden|Wenn diese Option aktiviert ist, werden Daten, die über die Verbindung übergeben wird verschlüsselt.|
|Serverzertifikat vertrauen|Wenn diese Option aktiviert ist, wird das Zertifikat des Servers überprüft werden. Zertifikat des Servers muss der richtige Hostname des Servers und von einer vertrauenswürdigen Zertifizierungsstelle ausgestellt.|
|Datenbank auswählen|Wählen Sie aus, oder geben Sie den Datenbanknamen ein, dem Sie zugreifen möchten.|
|Datenbankdatei als Datenbankname anfügen|Gibt den Namen der primären Datei für eine anfügbare Datenbank an. Diese Datenbank wird angefügt und als Standarddatenbank für die Datenquelle verwendet. Im ersten Textfeld in diesem Abschnitt geben Sie den Datenbanknamen für die angefügte Datenbank verwendet.<br/><br/>Geben Sie den vollständigen Pfad zur Datei in das Textfeld mit der Bezeichnung angefügt werden `Using the filename`, oder klicken Sie auf die `...` Schaltfläche, um die Datenbankdatei zu suchen.|
|Ändern des Kennworts|Zeigt das Dialogfeld von SQL Server-Kennwort ändern. |
|Verbindung testen|Klicken Sie auf diese Option, um eine Verbindung mit der angegebenen Datenquelle herzustellen. Wenn die Verbindung fehlschlägt, stellen Sie sicher, dass die Einstellungen richtig sind. Zum Beispiel können Rechtschreibfehler und die Unterscheidung nach Groß-/Kleinschreibung das Fehlschlagen von Verbindungen verursachen.|

## <a name="advanced-tab"></a>Registerkarte „Erweitert“
Verwenden Sie die Registerkarte "Erweitert", anzeigen und Festlegen von zusätzlichen Initialisierungseigenschaften.

![Screenshot des OLE DB Data Link-Seiten – Registerkarte "Erweitert"](../media/data-link-pages-advanced-tab.png)

|Option|und Beschreibung|
|---   |---        |
| Connect timeout | Gibt die Zeitspanne (in Sekunden) an, die zum Abschluss der Initialisierung der Microsoft OLE DB-Treiber für SQL Server wartet. Wenn es bei der Initialisierung zu einem Timeout kommt, wird ein Fehler zurückgegeben, und die Verbindung wird nicht hergestellt.|


> [!NOTE]  
>  Weitere allgemeine Informationen zur Data Link Verbindung finden Sie unter den [Data Link-API – Übersicht](https://go.microsoft.com/fwlink/?linkid=2067432).

## <a name="next-steps"></a>Nächste Schritte
- [Authentifizieren Sie sich bei Azure Active Directory](../features/using-azure-active-directory.md) mit dem OLE DB-Treiber.

- [Eingabeaufforderung für Anmeldeinformationen für die Authentifizierung für Benutzer](../help-topics/sql-server-login-dialog.md) mit dem OLE DB-Treiber.