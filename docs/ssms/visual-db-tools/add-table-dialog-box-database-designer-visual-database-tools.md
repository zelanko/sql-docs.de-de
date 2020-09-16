---
description: Tabelle hinzufügen (Dialogfeld) (Database Designer) (Visual Database Tools)
title: Dialogfeld „Tabelle hinzufügen“ (Datenbank-Designer)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65555
- vdt.dlgbox.schema.addtable
ms.assetid: 3c0b1b30-795c-4240-91d6-890b8348014a
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: 53898206b1111119dad7056e420bf7395d326007
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497331"
---
# <a name="add-table-dialog-box-database-designer-visual-database-tools"></a>Tabelle hinzufügen (Dialogfeld) (Database Designer) (Visual Database Tools)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Mit diesem Dialogfeld können Sie Tabellen im Datenbank-Designer hinzufügen.  
  
> [!NOTE]  
> Wenn die Tabelle zur Replikation veröffentlicht ist, müssen Sie mit der Transact-SQL-Anweisung [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) oder mit SMO (SQL Server Management Objects) Schemaänderungen ausführen. Wenn die Schemaänderungen mit dem Tabellen-Designer oder dem Datenbankdiagramm-Designer ausgeführt werden, wird versucht, die Tabelle zu entfernen und erneut zu erstellen. Da veröffentlichte Objekte nicht gelöscht werden können, schlägt die Schemaänderung fehl.  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächenelemente  
**Aktualisieren**  
Aktualisiert die Liste der Tabellen, sodass sie mit dem aktuellen Stand der Datenbank übereinstimmt.  
  
**Add (Hinzufügen)**  
Fügt die ausgewählten Tabellen hinzu.  
  
> [!NOTE]  
> Wenn Sie dem Diagramm mehrere Tabellen hinzufügen möchten, können Sie alle auswählen und dann auf **Hinzufügen**klicken. Sie können auch auf jede hinzuzufügende Tabelle doppelklicken und anschließend auf **Schließen** klicken.  
  
**Close**  
Schließt das Dialogfeld, ohne dass weitere Tabellen hinzugefügt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
[Hinzufügen von Tabellen zu Diagrammen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/add-tables-to-diagrams-visual-database-tools.md)  
  
