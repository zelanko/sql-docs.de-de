---
title: Grundlagen des Besitzes von Datenbankdiagrammen
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.CannotOpenWithInvalidOwner
helpviewer_keywords:
- diagrams [SQL Server], ownership
- database diagrams [SQL Server], ownership
- owners [SQL Server], database diagrams
ms.assetid: 4a27a48e-c4ef-4017-82b8-0cac4d0bbcac
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 170851e58273695a588b9359ba07460eab6d6884
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86004131"
---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a>Grundlagen des Besitzes von Datenbankdiagrammen (Visual Database Tools)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Der Datenbankdiagramm-Designer kann erst verwendet werden, nachdem er von einem Mitglied der db_owner-Rolle (eine Rolle von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken) für den Zugriff auf Diagramme eingerichtet wurde. Jedes Diagramm hat nur einen einzigen Besitzer, und zwar den Benutzer, der das Diagramm erstellt hat. Weitere Informationen zum Einrichten der Diagrammerstellung finden Sie im Artikel [Einrichten des Datenbankdiagramm-Designers(../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md).  
  
Es folgen einige Punkte, die Sie beim Besitz von Diagrammen beachten sollten:  
  
-   Obwohl jeder beliebige Benutzer mit Zugriff auf eine Datenbank ein Diagramm erstellen kann, können nur der Ersteller des Diagramms und alle Mitglieder der Rolle db_owner das Diagramm anzeigen.  
  
-   Der Besitz von Diagrammen kann nur an Mitglieder der Rolle db_owner übertragen werden. Und dies ist auch nur dann möglich, wenn der vorherige Besitzer des Diagramms aus der Datenbank entfernt wurde.  
  
-   Wenn der Besitzer eines Diagramms aus der Datenbank entfernt wurde, bleibt das Diagramm in der Datenbank, bis ein Mitglied der Rolle db_owner versucht, das Diagramm zu öffnen. Zu diesem Zeitpunkt kann das Mitglied von db_owner entscheiden, den Besitz des Diagramms zu übernehmen.  
  
## <a name="see-also"></a>Weitere Informationen

[Arbeiten mit Datenbankdiagrammen](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
[Einrichten des Datenbankdiagramm-Designers](../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md)