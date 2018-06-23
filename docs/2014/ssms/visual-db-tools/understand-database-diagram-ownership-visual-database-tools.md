---
title: Grundlagen des Besitzes von Datenbankdiagrammen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vdt.diagnostic.CannotOpenWithInvalidOwner
helpviewer_keywords:
- diagrams [SQL Server], ownership
- database diagrams [SQL Server], ownership
- owners [SQL Server], database diagrams
ms.assetid: 4a27a48e-c4ef-4017-82b8-0cac4d0bbcac
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6a05d1be7a194bd3ed47aed4936cdc51d479e81f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162175"
---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a>Grundlagen des Besitzes von Datenbankdiagrammen (Visual Database Tools)
  Der Datenbankdiagramm-Designer kann erst verwendet werden, nachdem er von einem Mitglied der db_owner-Rolle (eine Rolle von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbanken) für den Zugriff auf Diagramme eingerichtet wurde. Jedes Diagramm hat nur einen einzigen Besitzer, und zwar den Benutzer, der das Diagramm erstellt hat. Weitere Informationen zum Einrichten der diagrammerstellung finden Sie unter [Festlegen von Datenbankdiagramm-Designer &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
 Es folgen einige Punkte, die Sie beim Besitz von Diagrammen beachten sollten:  
  
-   Obwohl jeder beliebige Benutzer mit Zugriff auf eine Datenbank ein Diagramm erstellen kann, können nur der Ersteller des Diagramms und alle Mitglieder der Rolle db_owner das Diagramm anzeigen.  
  
-   Der Besitz von Diagrammen kann nur an Mitglieder der Rolle db_owner übertragen werden. Und dies ist auch nur dann möglich, wenn der vorherige Besitzer des Diagramms aus der Datenbank entfernt wurde.  
  
-   Wenn der Besitzer eines Diagramms aus der Datenbank entfernt wurde, bleibt das Diagramm in der Datenbank, bis ein Mitglied der Rolle db_owner versucht, das Diagramm zu öffnen. Zu diesem Zeitpunkt kann das Mitglied von db_owner entscheiden, den Besitz des Diagramms zu übernehmen.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Datenbankdiagrammen &#40;Visual Database Tools&#41;](work-with-database-diagrams-visual-database-tools.md)   
 [Einrichten im Datenbankdiagramm-Designer &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  