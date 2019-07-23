---
title: Entfernen von Tabellen aus Abfragen (Visual Database Tools)|Microsoft-Dokumente
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting tables
- removing tables
- dropping tables
- queries [SQL Server], tables
ms.assetid: 8fea0b4f-99b7-4050-8d6f-a97ffb839619
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b0b861034b3d95fd653358b91e31352776e1dad3
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68255988"
---
# <a name="remove-tables-from-queries-visual-database-tools"></a>Entfernen von Tabellen aus Abfragen (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Sie können eine Tabelle oder ein Tabellenwertobjekt aus der Abfrage entfernen.  
  
> [!NOTE]  
> Beim Entfernen einer Tabelle oder eines Tabellenwertobjekts wird das entsprechende Objekt nur aus der Abfrage entfernt und nicht aus der Datenbank selbst. Detaillierte Informationen zum Entfernen von Tabellen aus einer Datenbank finden Sie unter [Vorgehensweise: Löschen von Tabellen (Datenbank-Engine)](https://msdn.microsoft.com/ca6aa3e9-9885-44c3-bafc-aec441fd97ec).  
  
### <a name="to-remove-a-table-or-table-structured-object"></a>So entfernen Sie eine Tabelle oder ein Objekt mit Tabellenstruktur  
  
-   Wählen Sie im **Diagrammbereich**die Tabelle, die Sicht, die benutzerdefinierte Funktion, das Synonym oder die Abfrage aus, und drücken Sie anschließend ENTF, oder klicken Sie mit der rechten Maustaste auf das Objekt, und wählen Sie im daraufhin angezeigten Dialogfeld den Befehl **Entfernen** aus. Sie können mehrere Objekte auswählen und gleichzeitig entfernen.  
  
    -oder-  
  
-   Entfernen Sie im **SQL-Bereich**alle Verweise auf das Objekt.  
  
Wenn Sie eine Tabelle oder ein Tabellenwertobjekt entfernen, werden vom Abfrage- und Sicht-Designer Verknüpfungen mit dieser Tabelle oder diesem Tabellenwertobjekt automatisch entfernt. Außerdem werden Verweise auf die Spalten des Objekts aus dem **SQL-Bereich** und dem **Kriterienbereich**entfernt. Wenn die Abfrage jedoch komplexe, auf das Objekt bezogene Ausdrücke enthält, wird das Objekt erst nach dem Entfernen aller zugehörigen Verweise entfernt.  
  
## <a name="see-also"></a>Weitere Informationen  
[Hinzufügen von Tabellen zu Abfragen (Visual Database Tools)](../../ssms/visual-db-tools/add-tables-to-queries-visual-database-tools.md)  
[Erstellen von Tabellenaliasen (Visual Database Tools)](../../ssms/visual-db-tools/create-table-aliases-visual-database-tools.md)  
[Angeben von Suchkriterien (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[Zusammenfassen von Abfrageergebnissen (Visual Database Tools)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Ausführen grundlegender Vorgänge mit Abfragen (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
