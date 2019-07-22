---
title: Tabelle aktualisieren (Dialogfeld) (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.updatetable
- vdtsql.chm:69643
ms.assetid: 174c7275-5b15-42a9-b172-5ff30de575a1
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f2c3c1b59b43458bf6f24e5c255f43d7eb4cd92e
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68263120"
---
# <a name="update-table-dialog-box-visual-database-tools"></a>Tabelle aktualisieren (Dialogfeld) (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Mit diesem Dialogfeld können Sie die Tabelle angeben, die aktualisiert werden soll.  
  
Dieses Dialogfeld wird angezeigt, wenn beim Ändern eines Abfragetyps in eine Updateabfrage mehr als eine Tabelle im Diagrammbereich angezeigt wird.  
  
Wählen Sie die zu aktualisierende Tabelle aus, und wählen Sie dann **OK**aus.  
  
> [!NOTE]  
> Wenn die Tabelle zur Replikation veröffentlicht ist, müssen Sie mit der Transact-SQL-Anweisung [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) oder mit SMO (SQL Server Management Objects) Schemaänderungen ausführen. Wenn die Schemaänderungen mit dem Tabellen-Designer oder dem Datenbankdiagramm-Designer ausgeführt werden, wird versucht, die Tabelle zu entfernen und erneut zu erstellen. Da veröffentlichte Objekte nicht gelöscht werden können, schlägt die Schemaänderung fehl.  
  
## <a name="see-also"></a>Weitere Informationen  
[Erstellen von Updateabfragen (Visual Database Tools)](../../ssms/visual-db-tools/create-update-queries-visual-database-tools.md)  
  
