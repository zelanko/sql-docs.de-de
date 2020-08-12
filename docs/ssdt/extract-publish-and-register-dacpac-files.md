---
title: Extrahieren, Veröffentlichen und Registrieren von DACPAC-Dateien
description: Hier erfahren Sie mehr über die möglichen Aktionen mit Datenschichtanwendungen (DACs). Dazu zählen beispielsweise das Extrahieren, Veröffentlichen und Registrieren von Momentaufnahmedateien (DACPAC-Dateien).
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
f1_keywords:
- sql.data.tools.DacTableChooser
- sql.data.tools.DacPublishDialog
- sql.data.tools.DacPropertiesDialog
- sql.data.tools.publishdacproject
- sql.data.tools.DacExtractDialog
ms.assetid: ed900f93-d3df-40f5-8e62-4d722595e041
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: db4981480d5c14a658c49e29068f7eebfa53bb6b
ms.sourcegitcommit: b860fe41b873977649dca8c1fd5619f294c37a58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2020
ms.locfileid: "85518960"
---
# <a name="extract-publish-and-register-dacpac-files"></a>Extrahieren, Veröffentlichen und Registrieren von DACPAC-Dateien

In diesem Thema werden vier Vorgehensweisen beschrieben, die Sie durchführen können, indem Sie im SQL Server-Objekt-Explorer mit der rechten Maustaste auf eine verbundene Datenbank klicken:  
  
-   Datenebenenanwendung veröffentlichen  
  
-   Datenebenenanwendung extrahieren  
  
-   Datenebenenanwendung registrieren  
  
-   Registrierung der Datenebenenanwendung aufheben  
  
## <a name="publish-data-tier-application"></a>Datenebenenanwendung veröffentlichen  
Sie können eine DACPAC-Datei auf einer Datenbank veröffentlichen. Durch die Veröffentlichungsaktion wird ein Datenbankschema inkrementell aktualisiert, sodass es dem Schema einer DACPAC-Quelldatei entspricht. Wenn die Datenbank auf dem Server nicht vorhanden ist, wird sie durch den Veröffentlichungsvorgang erstellt.  
  
Diese Aktion ist auch verfügbar, wenn Sie den Knoten Datenbanken auswählen.  
  
Wählen Sie die DACPAC-Datei aus. Nachdem Sie eine DACPAC-Datei angegeben haben, ist die Schaltfläche **DAC-Eigenschaften** aktiviert. Im Dialogfeld **DAC-Eigenschaften** werden Informationen zur DACPAC-Datei angezeigt.  
  
Geben Sie die Verbindungszeichenfolge zum Datenbankserver und dann den Datenbanknamen an, sofern der Datenbankname nicht in der Verbindungszeichenfolge enthalten ist.  
  
Die Schaltflächen **Veröffentlichen** und **Skript generieren** sind jetzt aktiviert. Wenn Sie ein Skript generieren, wird es in einem Dokumentfenster geöffnet und kann nach Bedarf gespeichert werden. Wenn Sie direkt in der Datenbank veröffentlichen möchten, können Sie eine Zusammenfassung des Updates und das tatsächlich verwendete Skript im Fenster **Datentoolvorgänge** anzeigen.  
  
Wenn das Kontrollkästchen **Als Datenschichtanwendung registrieren** aktiviert ist, führt dies dazu, dass die resultierende Datenbank als Datenschichtanwendung in den Servermetadaten registriert wird. Falls die Datenbank, auf der Sie Inhalte veröffentlichen, registriert ist, kann die Veröffentlichung fehlschlagen, wenn sich das Schema der Datenbank von dem der aktuell registrierten DACPAC-Datei unterscheidet.  
  
Zusätzliche Konfigurationseinstellungen für die Veröffentlichung sind im Dialogfeld **Erweiterte Veröffentlichungseinstellungen** enthalten, das Sie durch Klicken auf die Schaltfläche **Erweitert** aufrufen können.  
  
## <a name="extract-data-tier-application"></a>Datenebenenanwendung extrahieren  
Sie können eine DACPAC-Datei aus einer Datenbank extrahieren. Durch das Extrahieren wird eine Datenbankmomentaufnahme (DACPAC-Datei) von einer SQL Server- oder Azure SQL-Livedatenbank erstellt, die zusätzlich zum Datenbankschema Daten aus Benutzertabellen enthalten kann.  
  
Geben Sie die zu erstellende DACPAC-Datei an. Über die Schaltfläche **DAC-Eigenschaften** wird das Dialogfeld **DAC-Eigenschaften** angezeigt, in dem Sie Eigenschaften der DACPAC-Datei festlegen können.  
  
Die Konfiguration des Extrahierungsvorgangs kann bei Bedarf geändert werden. Im Abschnitt **Einstellungen extrahieren** können Sie auswählen, ob Sie nur das Schema oder das Schema einschließlich der Tabellendaten extrahieren möchten. Wenn Sie das Schema und die Daten extrahieren möchten, können Sie die Tabellen auswählen, für die Daten extrahiert werden sollen.  
  
## <a name="register-data-tier-application"></a>Datenebenenanwendung registrieren  
Sie können eine Datenbank als Datenebenenanwendung (DAC) innerhalb der Instanz registrieren. Dadurch wird eine Darstellung des aktuellen Zustands des Datenbankschemas in den Systemmetadaten gespeichert.  
  
Geben Sie im Dialogfeld **Als Datenschichtanwendung registrieren** die Eigenschaften der registrierten DAC-Datei an.  
  
## <a name="unregister-data-tier-application"></a>Registrierung der Datenebenenanwendung aufheben  
Beim Aufheben der Registrierung können Sie die Metadaten einer registrierten Datenebenenanwendung aus der Instanz entfernen. Die registrierte Datenbank wird beim Aufheben der Registrierung nicht gelöscht.  
  
## <a name="see-also"></a>Weitere Informationen  
[Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md)  
  
