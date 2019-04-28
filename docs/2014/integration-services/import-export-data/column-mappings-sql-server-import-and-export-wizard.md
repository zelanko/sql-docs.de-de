---
title: Spaltenzuordnungen (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.columnmapandtransform.f1
ms.assetid: eadc54a6-f936-4ffc-91d7-fbfd2bdcab93
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0108004bc7fb5743ab92c455f4aee99a9f3df498
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62893041"
---
# <a name="column-mappings-sql-server-import-and-export-wizard"></a>Spaltenzuordnungen (SQL Server-Import/Export-Assistent)
  Verwenden der **Spaltenzuordnungen** Transformationsparameter bearbeiten im Dialogfeld.  
  
> [!NOTE]  
>  Sie müssen nicht alle Spalten in einer Tabelle kopieren, wenn Sie die Option zum Kopieren von Tabellen auswählen. Wählen Sie  **\<ignorieren >** in die **Ziel** dieses Dialogfeld für Spalten, die übersprungen werden sollen.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import / Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen zum Starten des Assistenten als auch die Berechtigungen erforderlich, um den Assistenten erfolgreich ausführen, finden Sie unter [führen Sie die SQL Server-Import / Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem SQL Server-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Optionen  
 **Quelle**  
 Identifiziert die ausgewählte Quelltabelle, -sicht oder -abfrage.  
  
 **Ziel**  
 Identifiziert die ausgewählte Zieltabelle, -sicht oder -abfrage.  
  
 **Create destination table/file**  
 Geben Sie an, ob eine Zieltabelle erstellt werden soll, falls noch keine solche Tabelle vorhanden ist.  
  
 **Delete rows in destination table/file**  
 Geben Sie an, ob die Daten aus einer vorhandenen Tabelle gelöscht werden sollen, bevor neue Daten geladen werden.  
  
 **Append rows to destination table/file**  
 Geben Sie an, ob die neuen Daten an die in der Tabelle bereits enthaltenen Daten angefügt werden sollen.  
  
 **SQL bearbeiten**  
 Verwenden Sie die standardanweisung im der **SQL­Anweisung Create Table** Dialogfeld, oder ändern Sie sie für Ihre Zwecke. Wenn die Anweisung geändert wird, müssen Sie auch für die Tabellenzuordnung die entsprechenden Änderungen vornehmen.  
  
 **Zieltabelle löschen und erneut erstellen**  
 Wählen Sie diese Option aus, um die Zieltabelle zu überschreiben. Diese Option ist nur verfügbar, wenn Sie den Assistenten verwenden, um die Zieltabelle zu erstellen. Die Zieltabelle wird nur gelöscht und erneut erstellt, wenn Sie das vom Assistenten erstellte Paket speichern und anschließend erneut ausführen.  
  
 **IDENTITY_INSERT aktivieren**  
 Wählen Sie diese Option aus, damit vorhandene IDENTITY-Werte in den Quelldaten in eine IDENTITY-Spalte in der Zieltabelle eingefügt werden können. Standardmäßig ist dies für die Identity-Zielspalte nicht zulässig.  
  
 **Zuordnungen**  
 Zeigt an wie jede Spalte in der Datenquelle einer Spalte im Ziel zugeordnet wird.  
  
 Diese Liste weist die folgenden Spalten auf:  
  
 **Quelle**  
 Zeigen Sie die einzelnen Quellspalten an, für die Transformationsparameter festgelegt werden können.  
  
 **Ziel**  
 Geben Sie an, ob eine Spalte während des Kopiervorgangs ignoriert werden soll. Sie können nur eine Teilmenge der Spalten kopieren, indem Sie auswählen  **\<ignorieren >** in dieser Spalte für Spalten, die übersprungen werden sollen. Bevor Sie Spalten zuordnen, müssen Sie alle Spalten ignorieren, die nicht zugeordnet werden.  
  
 **Typ**  
 Wählen Sie einen Datentyp für die Spalte aus.  
  
 **NULL zulassen**  
 Geben Sie an, ob der NULL-Wert in der Spalte zulässig ist.  
  
 **Größe**  
 Geben Sie die Anzahl der Zeichen in der Spalte an.  
  
 **Genauigkeit**  
 Geben Sie die Genauigkeit der angezeigten Daten in der Anzahl der Ziffern an.  
  
 **Dezimalstellen**  
 Geben Sie die Anzahl der Dezimalstellen der angezeigten Daten an.  
  
  
