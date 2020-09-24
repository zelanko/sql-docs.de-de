---
title: Erweiterung „SQL Server Import“
description: Erfahren Sie, wie Sie die Erweiterung „SQL Server Import“ für Azure Data Studio installieren und verwenden, einen Assistenten, der TXT- und CSV-Dateien in eine SQL-Tabelle konvertiert.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.reviewer: maghan, sstein
ms.custom: ''
ms.date: 09/22/2020
ms.openlocfilehash: caf2b3ee70d2542dc529e83e1e243ff215c644a4
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91123098"
---
# <a name="sql-server-import-extension"></a>Erweiterung „SQL Server Import“

Die Erweiterung „SQL Server Import“ konvertiert TXT- und CSV-Dateien in eine SQL-Tabelle. Der Assistent nutzt das Microsoft Research-Framework [PROSE (Program Synthesis using Examples)](https://microsoft.github.io/prose/), um die Dateien mit minimalen Benutzereingaben auf intelligente Weise zu analysieren. PROSE ist ein leistungsstarkes Framework für Data Wrangling und die Technologie, auf der die Blitzvorschau in Microsoft Excel basiert.

Informationen über die SSMS-Version dieses Features finden Sie in [diesem Artikel](../../relational-databases/import-export/import-flat-file-wizard.md).

## <a name="install-the-sql-server-import-extension"></a>Installieren der Erweiterung „SQL Server Import“

1. Um den Erweiterungs-Manager zu öffnen und auf die verfügbaren Erweiterungen zuzugreifen, klicken Sie auf das Symbol für Erweiterungen, oder wählen Sie im Menü **Ansicht** den Befehl **Erweiterungen** aus.
2. Wählen Sie eine verfügbare Erweiterung aus, um deren Details anzuzeigen.

   ![Erweiterungs-Manager mit Erweiterung für den Import](media/sql-server-import-extension/import-wizard-install.png)

3. Wählen Sie die gewünschte Erweiterung aus, und **installieren** Sie diese.
4. Klicken Sie auf **Erneut laden**, um die Erweiterung zu aktivieren (nur bei der Erstinstallation einer Erweiterung erforderlich).

## <a name="start-import-wizard"></a>Starten des Import-Assistenten

1. Um SQL Server Import zu starten, stellen Sie zunächst auf der Registerkarte „Server“ eine Verbindung mit einem Server her.
2. Wenn die Verbindung hergestellt ist, zeigen Sie die Detailinformationen zu der Zieldatenbank an, aus der Sie eine Datei in eine SQL-Tabelle importieren möchten.
3. Klicken Sie mit der rechten Maustaste auf die Datenbank, und klicken Sie dann auf **Import Wizard** (Import-Assistent).

    ![Import wizard (Import-Assistent)](media/sql-server-import-extension/open-import-wizard.png)

## <a name="importing-a-file"></a>Importieren einer Datei

1. Wenn Sie mit der rechten Maustaste klicken, um den Assistenten zu starten, sind Server und Datenbank bereits automatisch ausgefüllt. Wenn weitere aktive Verbindungen bestehen, können Sie diese in der Dropdownliste auswählen. 

    Wählen Sie eine Datei aus, indem Sie auf **Durchsuchen** klicken. Der Tabellenname sollte basierend auf dem Dateinamen bereits automatisch ausgefüllt sein, Sie können ihn aber auch selbst ändern.

    Das Schema lautet standardmäßig „dbo“, Sie können es jedoch ändern. Klicken Sie auf **Weiter**, um fortzufahren.

    ![Eingabedatei](media/sql-server-import-extension/import-wizard-input-file.png)

2. Der Assistent generiert eine Vorschau basierend auf den ersten 50 Zeilen. Auf dieser Seite sind keine weiteren Aktionen erforderlich, außer zu überprüfen, ob die Daten richtig aussehen. Klicken Sie auf **Weiter**, um fortzufahren.

    ![Datenvorschau](media/sql-server-import-extension/import-wizard-preview-data.png)

3. Auf dieser Seite können Sie Änderungen an den folgenden Informationen vornehmen: dem Spaltennamen, dem Datentyp, der Angabe, ob es sich um einen Primärschlüssel handelt, und der Angabe, ob NULL-Werte zulässig sind. Sie können so viele Änderungen vornehmen, wie Sie wünschen. Klicken Sie auf **Daten importieren**, um fortzufahren.

    ![Spalten ändern](media/sql-server-import-extension/import-wizard-modify-columns.png)

4. Diese Seite bietet eine Zusammenfassung der ausgewählten Aktionen. Sie können auch ermitteln, ob Ihre Tabelle erfolgreich eingefügt wurde oder nicht.

    Sie können auf **Fertig, Zurück** klicken, wenn Sie Änderungen vornehmen müssen, oder auf **Neue Datei importieren**, um schnell eine weitere Datei zu importieren.

    ![Zusammenfassung](media/sql-server-import-extension/import-wizard-summary.png)

5. Überprüfen Sie, ob Ihre Tabelle erfolgreich importiert wurde, indem Sie Ihre Zieldatenbank aktualisieren oder eine SELECT-Query für den Tabellennamen ausführen.

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen über den Import-Assistenten finden Sie in diesem [Blogbeitrag](https://cloudblogs.microsoft.com/sqlserver/2018/08/30/the-august-release-of-sql-operations-studio-is-now-available/).
- Weitere Informationen über PROSE finden Sie in der [Dokumentation](https://microsoft.github.io/prose/).