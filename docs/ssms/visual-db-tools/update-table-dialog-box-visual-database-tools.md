---
title: Tabelle aktualisieren (Dialogfeld) (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.updatetable
- vdtsql.chm:69643
ms.assetid: 174c7275-5b15-42a9-b172-5ff30de575a1
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 043d5c7430663fd1f12b20dbaa73ec7aa4da817e
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "42775317"
---
# <a name="update-table-dialog-box-visual-database-tools"></a>Tabelle aktualisieren (Dialogfeld) (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Mit diesem Dialogfeld können Sie die Tabelle angeben, die aktualisiert werden soll.  
  
Dieses Dialogfeld wird angezeigt, wenn beim Ändern eines Abfragetyps in eine Updateabfrage mehr als eine Tabelle im Diagrammbereich angezeigt wird.  
  
Wählen Sie die zu aktualisierende Tabelle aus, und wählen Sie dann **OK**aus.  
  
> [!NOTE]  
> Wenn die Tabelle zur Replikation veröffentlicht ist, müssen Sie mit der Transact-SQL-Anweisung [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) oder mit SMO (SQL Server Management Objects) Schemaänderungen ausführen. Wenn die Schemaänderungen mit dem Tabellen-Designer oder dem Datenbankdiagramm-Designer ausgeführt werden, wird versucht, die Tabelle zu entfernen und erneut zu erstellen. Da veröffentlichte Objekte nicht gelöscht werden können, schlägt die Schemaänderung fehl.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Erstellen von Updateabfragen (Visual Database Tools)](../../ssms/visual-db-tools/create-update-queries-visual-database-tools.md)  
  
