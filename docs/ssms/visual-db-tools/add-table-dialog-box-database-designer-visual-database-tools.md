---
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
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: 9fcd2f3dbb1d0eca44a1cc5025239b81de26b24f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75253414"
---
# <a name="add-table-dialog-box-database-designer-visual-database-tools"></a>Tabelle hinzufügen (Dialogfeld) (Database Designer) (Visual Database Tools)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Mit diesem Dialogfeld können Sie Tabellen im Datenbank-Designer hinzufügen.  
  
> [!NOTE]  
> Wenn die Tabelle zur Replikation veröffentlicht ist, müssen Sie mit der Transact-SQL-Anweisung [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) oder mit SMO (SQL Server Management Objects) Schemaänderungen ausführen. Wenn die Schemaänderungen mit dem Tabellen-Designer oder dem Datenbankdiagramm-Designer ausgeführt werden, wird versucht, die Tabelle zu entfernen und erneut zu erstellen. Da veröffentlichte Objekte nicht gelöscht werden können, schlägt die Schemaänderung fehl.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
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
  
