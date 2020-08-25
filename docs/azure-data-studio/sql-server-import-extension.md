---
title: Erweiterung „SQL Server Import“
description: Erfahren Sie, wie Sie die SQL Server Import-Erweiterung (Vorschau) für Azure Data Studio installieren und verwenden, einen Assistenten, der TXT-und CSV-Dateien in eine SQL-Tabelle konvertiert.
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu, maghan, sstein
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 9ecee71588cb54cb23c813cf5009b92159cf94d6
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88765919"
---
# <a name="sql-server-import-extension-preview"></a>Erweiterung „SQL Server Import“ (Vorschau)

Die Erweiterung „SQL Server Import“ (Vorschau) konvertiert TXT- und CSV-Dateien in eine SQL-Tabelle. Der Assistent nutzt das Microsoft Research-Framework [PROSE (Program Synthesis using Examples)](https://microsoft.github.io/prose/), um die Dateien mit minimalen Benutzereingaben auf intelligente Weise zu analysieren. PROSE stellt ein leistungsstarkes Framework für das Data Wrangling dar und ist die gleiche Technologie, auf der die Blitzvorschau in Microsoft Excel basiert.

Informationen über die SSMS-Version dieses Features finden Sie in [diesem Artikel](../relational-databases/import-export/import-flat-file-wizard.md).


## <a name="install-the-sql-server-import-extension"></a>Installieren der Erweiterung „SQL Server Import“

1. Um den Erweiterungs-Manager zu öffnen und auf die verfügbaren Erweiterungen zuzugreifen, klicken Sie auf das Symbol für Erweiterungen, oder wählen Sie im Menü **Ansicht** den Befehl **Erweiterungen** aus.
2. Wählen Sie eine verfügbare Erweiterung aus, um deren Details anzuzeigen.

   ![Erweiterungs-Manager mit Erweiterung für den Import](media/sql-server-import-extension/import-wizard-install.png)

1. Wählen Sie die gewünschte Erweiterung aus, und **installieren** Sie diese.
2. Klicken Sie auf **Erneut laden**, um die Erweiterung zu aktivieren (nur bei der Erstinstallation einer Erweiterung erforderlich).

## <a name="start-import-wizard"></a>Starten des Import-Assistenten

1. Um SQL Server Import zu starten, stellen Sie zunächst auf der Registerkarte „Server“ eine Verbindung mit einem Server her.
2. Wenn die Verbindung hergestellt ist, zeigen Sie die Detailinformationen zu der Zieldatenbank an, aus der Sie eine Datei in eine SQL-Tabelle importieren möchten.
3. Klicken Sie mit der rechten Maustaste auf die Datenbank, und klicken Sie auf **Import-Assistent**.
    ![Offener Import-Assistent](media/sql-server-import-extension/open-import-wizard.png)

## <a name="importing-a-file"></a>Importieren einer Datei
1. Wenn Sie mit der rechten Maustaste klicken, um den Assistenten zu starten, sind Server und Datenbank bereits automatisch ausgefüllt. Wenn weitere aktive Verbindungen bestehen, können Sie diese in der Dropdownliste auswählen. 
    
    Wählen Sie eine Datei aus, indem Sie auf **Durchsuchen** klicken. Der Tabellenname sollte basierend auf dem Dateinamen bereits automatisch ausgefüllt sein, Sie können den Namen aber auch selbst ändern.

    Das Schema lautet standardmäßig „dbo“, Sie können es jedoch ändern. Klicken Sie zum Fortfahren auf **Weiter** .
    ![Eingabedatei](media/sql-server-import-extension/import-wizard-input-file.png)
1. Der Assistent generiert eine Vorschau basierend auf den ersten 50 Zeilen. Auf dieser Seite sind keine weiteren Aktionen erforderlich, außer, dass Sie überprüfen müssen, ob die Daten richtig aussehen. Klicken Sie zum Fortfahren auf **Weiter** .
    ![Offener Import-Assistent](media/sql-server-import-extension/import-wizard-preview-data.png)
2. Auf dieser Seite können Sie einige Änderungen vornehmen, z.B. für den Spaltennamen, den Datentyp, die Angabe, ob es sich um einen Primärschlüssel handelt, und Angaben dazu, ob NULL-Werte zugelassen sin. Sie können so viele Änderungen vornehmen, wie Sie wünschen. Klicken Sie auf **Daten importieren**, um fortzufahren.
    ![Offener Import-Assistent](media/sql-server-import-extension/import-wizard-modify-columns.png)
3. Diese Seite bietet eine Zusammenfassung der ausgewählten Aktionen. Sie können auch ermitteln, ob Ihre Tabelle erfolgreich eingefügt wurde oder nicht. 

    Sie können auf **Zurück** klicken, wenn Sie Änderungen vornehmen müssen, oder Sie klicken auf **Neue Datei importieren**, um schnell eine weitere Datei zu importieren.
    ![Offener Import-Assistent](media/sql-server-import-extension/import-wizard-summary.png)
1. Überprüfen Sie, ob Ihre Tabelle erfolgreich importiert wurde, indem Sie Ihre Zieldatenbank aktualisieren oder eine SELECT-Query für den Tabellennamen ausführen.

## <a name="next-steps"></a>Nächste Schritte
- Weitere Informationen über den Import-Assistenten finden Sie in diesem [Blogbeitrag](https://cloudblogs.microsoft.com/sqlserver/2018/08/30/the-august-release-of-sql-operations-studio-is-now-available/).
- Weitere Informationen über PROSE finden Sie in der [Dokumentation](https://microsoft.github.io/prose/).