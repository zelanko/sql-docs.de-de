---
title: Grundlagen des Besitzes von Datenbankdiagrammen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.CannotOpenWithInvalidOwner
helpviewer_keywords:
- diagrams [SQL Server], ownership
- database diagrams [SQL Server], ownership
- owners [SQL Server], database diagrams
ms.assetid: 4a27a48e-c4ef-4017-82b8-0cac4d0bbcac
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6056a5136d8aceab338a18b32ecfac35a1af0364
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63204715"
---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a>Grundlagen des Besitzes von Datenbankdiagrammen (Visual Database Tools)
  Der Datenbankdiagramm-Designer kann erst verwendet werden, nachdem er von einem Mitglied der db_owner-Rolle (eine Rolle von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbanken) für den Zugriff auf Diagramme eingerichtet wurde. Jedes Diagramm hat nur einen einzigen Besitzer, und zwar den Benutzer, der das Diagramm erstellt hat. Weitere Informationen zum Einrichten der diagrammerstellung finden Sie unter [einrichten Diagramm des Designers &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
 Es folgen einige Punkte, die Sie beim Besitz von Diagrammen beachten sollten:  
  
-   Obwohl jeder beliebige Benutzer mit Zugriff auf eine Datenbank ein Diagramm erstellen kann, können nur der Ersteller des Diagramms und alle Mitglieder der Rolle db_owner das Diagramm anzeigen.  
  
-   Der Besitz von Diagrammen kann nur an Mitglieder der Rolle db_owner übertragen werden. Und dies ist auch nur dann möglich, wenn der vorherige Besitzer des Diagramms aus der Datenbank entfernt wurde.  
  
-   Wenn der Besitzer eines Diagramms aus der Datenbank entfernt wurde, bleibt das Diagramm in der Datenbank, bis ein Mitglied der Rolle db_owner versucht, das Diagramm zu öffnen. Zu diesem Zeitpunkt kann das Mitglied von db_owner entscheiden, den Besitz des Diagramms zu übernehmen.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Datenbankdiagrammen &#40;Visual Database Tools&#41;](work-with-database-diagrams-visual-database-tools.md)   
 [Einrichten im Datenbankdiagramm-Designer &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  
