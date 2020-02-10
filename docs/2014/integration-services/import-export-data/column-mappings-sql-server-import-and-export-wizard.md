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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62893041"
---
# <a name="column-mappings-sql-server-import-and-export-wizard"></a>Spaltenzuordnungen (SQL Server-Import/Export-Assistent)
  Verwenden Sie das Dialogfeld **Spalten** Zuordnungen, um Transformationsparameter zu bearbeiten.  
  
> [!NOTE]  
>  Sie müssen nicht alle Spalten in einer Tabelle kopieren, wenn Sie die Option zum Kopieren von Tabellen auswählen. Wählen ** \<** Sie in der Spalte **Ziel** dieses Dialog Felds für Spalten, die Sie überspringen möchten, die Option>ignorieren aus.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import/Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen für das Starten des Assistenten sowie zu den Berechtigungen, die zum erfolgreichen Ausführen des Assistenten erforderlich sind, finden Sie unter [Ausführen des SQL Server-Import/Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem SQL Server-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Tastatur  
 **`Source`**  
 Identifiziert die ausgewählte Quelltabelle, -sicht oder -abfrage.  
  
 **Ziel**  
 Identifiziert die ausgewählte Zieltabelle, -sicht oder -abfrage.  
  
 **Ziel Tabelle/-Datei erstellen**  
 Geben Sie an, ob eine Zieltabelle erstellt werden soll, falls noch keine solche Tabelle vorhanden ist.  
  
 **Zeilen in Ziel Tabelle/-Datei löschen**  
 Geben Sie an, ob die Daten aus einer vorhandenen Tabelle gelöscht werden sollen, bevor neue Daten geladen werden.  
  
 **Zeilen an Ziel Tabelle/-Datei anfügen**  
 Geben Sie an, ob die neuen Daten an die in der Tabelle bereits enthaltenen Daten angefügt werden sollen.  
  
 **SQL bearbeiten**  
 Verwenden Sie die default-Anweisung im Dialogfeld **SQL-Anweisung CREATE TABLE** , oder ändern Sie Sie für Ihre Zwecke. Wenn die Anweisung geändert wird, müssen Sie auch für die Tabellenzuordnung die entsprechenden Änderungen vornehmen.  
  
 **Ziel Tabelle löschen und erneut erstellen**  
 Wählen Sie diese Option aus, um die Zieltabelle zu überschreiben. Diese Option ist nur verfügbar, wenn Sie den Assistenten verwenden, um die Zieltabelle zu erstellen. Die Zieltabelle wird nur gelöscht und erneut erstellt, wenn Sie das vom Assistenten erstellte Paket speichern und anschließend erneut ausführen.  
  
 **Aktivieren der Identitäts Einfügung**  
 Wählen Sie diese Option aus, damit vorhandene IDENTITY-Werte in den Quelldaten in eine IDENTITY-Spalte in der Zieltabelle eingefügt werden können. Standardmäßig ist dies für die Identity-Zielspalte nicht zulässig.  
  
 **Zuordnungen**  
 Zeigt an wie jede Spalte in der Datenquelle einer Spalte im Ziel zugeordnet wird.  
  
 Diese Liste weist die folgenden Spalten auf:  
  
 **`Source`**  
 Zeigen Sie die einzelnen Quellspalten an, für die Transformationsparameter festgelegt werden können.  
  
 **Ziel**  
 Geben Sie an, ob eine Spalte während des Kopiervorgangs ignoriert werden soll. Sie können nur eine Teilmenge von Spalten kopieren, indem Sie in dieser Spalte für Spalten, die Sie überspringen möchten, die Option ** \<>ignorieren** auswählen. Bevor Sie Spalten zuordnen, müssen Sie alle Spalten ignorieren, die nicht zugeordnet werden.  
  
 **Typ**  
 Wählen Sie einen Datentyp für die Spalte aus.  
  
 **Nullable**  
 Geben Sie an, ob der NULL-Wert in der Spalte zulässig ist.  
  
 **Größe**  
 Geben Sie die Anzahl der Zeichen in der Spalte an.  
  
 **Präziser**  
 Geben Sie die Genauigkeit der angezeigten Daten in der Anzahl der Ziffern an.  
  
 **Migen**  
 Geben Sie die Anzahl der Dezimalstellen der angezeigten Daten an.  
  
  
