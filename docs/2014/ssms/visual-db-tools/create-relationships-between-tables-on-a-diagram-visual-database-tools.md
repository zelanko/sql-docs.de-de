---
title: Erstellen von Beziehungen zwischen Tabellen in einem Diagramm (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- diagrams [SQL Server], designing
ms.assetid: 28e9630c-dff4-46cc-bb0e-fe77998b6ac2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ab36ebfefbfd3d8cee8e6da7caadf86eb4a10032
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63184277"
---
# <a name="create-relationships-between-tables-on-a-diagram-visual-database-tools"></a>Erstellen von Beziehungen zwischen Tabellen in einem Diagramm (Visual Database Tools)
  Sie können im Datenbank-Designer Beziehungen zwischen den Spalten in verschiedenen Tabellen erstellen, indem Sie Spalten zwischen Tabellen ziehen.  
  
### <a name="to-create-a-relationship-graphically"></a>So erstellen Sie eine Beziehung grafisch  
  
1.  Klicken Sie im Datenbank-Designer auf die Zeilenauswahl, um eine oder mehrere Datenbankspalten auszuwählen, für die Sie eine Beziehung mit einer Spalte in einer anderen Tabelle erstellen möchten.  
  
2.  Ziehen Sie die Spalte(n) auf die zugehörige Tabelle.  
  
3.  Es werden zwei Dialogfelder angezeigt: **Fremdschlüsselbeziehung** und **Tabellen und Spalten**, wobei letzteres im Vordergrund angezeigt wird.  
  
4.  Unter**Beziehungsname** wird ein vom System bereitgestellter Name im Format FK_*localtable*_*foreigntable*angegeben. Sie können diesen Wert ändern.  
  
5.  Stellen Sie sicher, dass für **Primärschlüsseltabelle** die richtige Tabelle angegeben ist.  
  
6.  Im Raster sind alle lokalen Spalten und die entsprechenden Fremdspalten aufgeführt. Sie können Spalten hinzufügen oder entfernen bzw. die Zuordnungen ändern.  
  
7.  Wählen Sie **OK**aus.  
  
     Das Dialogfeld **Fremdschlüsselbeziehung** wird angezeigt. Unter**Ausgewählte Beziehung** wird die von Ihnen erstellte Beziehung angezeigt.  
  
8.  Sie können die Eigenschaften der Beziehung im Raster ändern.  
  
9. Klicken Sie auf **OK** , um die Beziehung zu erstellen.  
  
     Im Datenbank-Designer wird eine Beziehung zwischen von Ihnen ausgewählten Spalten gezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellen und Spalten Dialogfeld &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Unique- und Check-Einschränkungen](../../relational-databases/tables/unique-constraints-and-check-constraints.md)   
 [Verwenden von Tabellen in Datenbankdiagrammen &#40;Visual Database Tools&#41;](work-with-tables-in-database-diagram-visual-database-tools.md)  
  
  
