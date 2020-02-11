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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63184277"
---
# <a name="create-relationships-between-tables-on-a-diagram-visual-database-tools"></a>Erstellen von Beziehungen zwischen Tabellen in einem Diagramm (Visual Database Tools)
  Sie können im Datenbank-Designer Beziehungen zwischen den Spalten in verschiedenen Tabellen erstellen, indem Sie Spalten zwischen Tabellen ziehen.  
  
### <a name="to-create-a-relationship-graphically"></a>So erstellen Sie eine Beziehung grafisch  
  
1.  Klicken Sie im Datenbank-Designer auf die Zeilenauswahl, um eine oder mehrere Datenbankspalten auszuwählen, für die Sie eine Beziehung mit einer Spalte in einer anderen Tabelle erstellen möchten.  
  
2.  Ziehen Sie die Spalte(n) auf die zugehörige Tabelle.  
  
3.  Es werden zwei Dialogfelder angezeigt: **Fremdschlüsselbeziehung** und **Tabellen und Spalten**, wobei letzteres im Vordergrund angezeigt wird.  
  
4.  Der **Beziehungs Name** hat einen vom System bereitgestellten Namen im Format FK_*localtable*_*fremdntable*. Sie können diesen Wert ändern.  
  
5.  Stellen Sie sicher, dass für **Primärschlüsseltabelle** die richtige Tabelle angegeben ist.  
  
6.  Im Raster sind alle lokalen Spalten und die entsprechenden Fremdspalten aufgeführt. Sie können Spalten hinzufügen oder entfernen bzw. die Zuordnungen ändern.  
  
7.  Wählen Sie **OK**aus.  
  
     Das Dialogfeld **Fremdschlüsselbeziehung** wird angezeigt. **Ausgewählte Beziehung** zeigt die Beziehung an, die Sie erstellt haben.  
  
8.  Sie können die Eigenschaften der Beziehung im Raster ändern.  
  
9. Klicken Sie auf **OK** , um die Beziehung zu erstellen.  
  
     Im Datenbank-Designer wird eine Beziehung zwischen von Ihnen ausgewählten Spalten gezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellen und Spalten (Dialog Feld) &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Unique-Einschränkungen und Check-Einschränkungen](../../relational-databases/tables/unique-constraints-and-check-constraints.md)   
 [Verwenden von Tabellen in Datenbankdiagrammen &#40;Visual Database Tools&#41;](work-with-tables-in-database-diagram-visual-database-tools.md)  
  
  
