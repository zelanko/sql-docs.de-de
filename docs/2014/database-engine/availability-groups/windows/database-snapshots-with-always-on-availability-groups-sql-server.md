---
title: Datenbankmomentaufnahmen bei AlwaysOn-Verfügbarkeitsgruppen (SQLServer) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- database snapshots [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 7432da1c-ce2f-4cd9-af41-54c97744166b
caps.latest.revision: 5
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: a9db739495dc8f11c77d518815fe46d1b7f03e01
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047264"
---
# <a name="database-snapshots-with-alwayson-availability-groups-sql-server"></a>Datenbankmomentaufnahmen bei AlwaysOn-Verfügbarkeitsgruppen (SQL Server)
  Sie können auf einer primären oder sekundären Datenbank in einer Verfügbarkeitsgruppe eine Datenbankmomentaufnahme erstellen. Die Replikatrolle muss entweder PRIMARY oder SECONDARY sein und darf nicht den Status RESOLVING aufweisen.  
  
 Der Datenbanksynchronisierungsstatus sollte SYNCHRONIZING oder SYNCHRONIZED sein, wenn Sie eine Datenbankmomentaufnahme erstellen. Datenbankmomentaufnahmen können jedoch auch erstellt werden, wenn der Datenbanksynchronisierungsstatus NOT SYNCHRONIZING lautet.  
  
 Eine Datenbankmomentaufnahme auf einem sekundären Replikat sollte weiterhin funktionieren, wenn das Replikat mit DISCONNECTED vom primären Replikat getrennt wird.  
  
 Einige [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Bedingungen bewirken, dass sowohl die Quelldatenbank als auch deren Datenbankmomentaufnahmen neu gestartet werden, wobei die Verbindung für Benutzer vorübergehend getrennt wird. Nachfolgend sind diese Bedingungen aufgeführt:  
  
-   Das primäre Replikat ändert Rollen, entweder, weil das aktuelle primäre Replikat offline und dann auf der gleichen Serverinstanz wieder online geschaltet wird, oder weil die Verfügbarkeitsgruppe ein Failover ausführt.  
  
-   Die Datenbank wechselt zur sekundäre Rolle.  
  
 Wenn das Verfügbarkeitsreplikat, das Datenbankmomentaufnahmen hostet, ein Failover ausgeführt hat, bleiben die Datenbankmomentaufnahmen auf der Serverinstanz, auf der sie erstellt wurden. Benutzer können die Momentaufnahmen nach dem Failover weiter verwenden. Wenn die Leistung in Ihrer Umgebung wichtig ist, empfiehlt es sich, dass Sie Datenbankmomentaufnahmen nur auf sekundären Datenbanken erstellen, die von einem sekundären Replikat gehostet werden, das für manuellen Failovermodus konfiguriert ist.  Sollte es je zu einem manuellen Failover der Verfügbarkeitsgruppe zu diesem sekundären Replikat kommen, können Sie auf einem anderen sekundären Replikat einen neuen Satz von Datenbankmomentaufnahmen erstellen, Clients an die neuen Datenbankmomentaufnahmen umleiten und alle Datenbankmomentaufnahmen aus den jetzt primären Datenbanken löschen.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Datenbank-Momentaufnahmen &#40;SQL Server&#41;](../../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  