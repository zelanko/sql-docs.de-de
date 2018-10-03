---
title: Datenbankintegrität überprüfen (Task) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.checkdatabaseintegritytask.f1
helpviewer_keywords:
- data integrity [Integration Services]
- Check Database Integrity task [Integration Services]
- checking database consistency
- database consistency checks [Integration Services]
- verifying database consistency
- integrity checking [Integration Services]
ms.assetid: 5a82fe99-4503-429f-9337-e6bac7649fe4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cba77106e1aba2ee9c5e4bf2671d32137b09e27f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48123340"
---
# <a name="check-database-integrity-task"></a>Datenbankintegrität überprüfen (Task)
  Der Task Datenbankintegrität überprüfen überprüft die Zuordnung und strukturelle Integrität aller Objekte in der angegebenen Datenbank. Mit dem Task können Sie eine einzelne Datenbank oder mehrere Datenbanken überprüfen und auswählen, ob auch die Datenbankindizes überprüft werden sollen.  
  
 Der Task "Datenbankintegrität überprüfen" kapselt die DBCC CHECKDB-Anweisung. Weitere Informationen finden Sie unter [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql).  
  
## <a name="configuration-of-the-check-database-integrity-task"></a>Konfiguration des Tasks "Datenbankintegrität überprüfen"  
 Eigenschaften können Sie mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer festlegen. Dieser Task ist im **-Designer in der** Toolbox **im Abschnitt** Wartungsplantasks [!INCLUDE[ssIS](../../../includes/ssis-md.md)] enthalten.  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Task 'Datenbankintegrität überprüfen' &#40;Wartungsplan&#41;](../../relational-databases/maintenance-plans/check-database-integrity-task-maintenance-plan.md)  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer zu erhalten:  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md)  
  
  
