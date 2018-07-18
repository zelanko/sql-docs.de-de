---
title: Umbenennen von Anmeldungen, die mit Namen fester Serverrollen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- user-defined login names [SQL Server]
- fixed server roles [SQL Server]
- renamed logins [SQL Server]
- logins [SQL Server], names
ms.assetid: 10a1d77c-3153-474f-a6a0-969556794467
caps.latest.revision: 18
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0064e08000454f485846b45fb0cc3d37c0afd031
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155611"
---
# <a name="rename-logins-matching-fixed-server-role-names"></a>Umbenennen von Anmeldungen, die mit Namen fester Serverrollen identisch sind
  Der Upgrade Advisor hat einen oder mehrere benutzerdefinierte Anmeldenamen erkannt, die mit den Namen fester Serverrollen identisch sind. Namen fester Serverrollen sind reserviert. Benennen Sie den Anmeldenamen um, bevor Sie ein Upgrade durchführen.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Die folgenden Namen von festen Serverrollen sind reserviert und können nicht als benutzerdefinierte Anmeldenamen verwendet werden.  
  
-   **sysadmin**  
  
-   **serveradmin**  
  
-   **setupadmin**  
  
-   **securityadmin**  
  
-   **processadmin**  
  
-   **dbcreator**  
  
-   **diskadmin**  
  
-   **bulkadmin**  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Führen Sie vor dem Upgrade die folgenden Schritte aus:  
  
1.  Erfassen Sie die Sicherheits-IDs (SIDs) der Anmeldungen durch Ausführen der folgenden Anweisung.  
  
    ```  
    SELECT name, sid   
    FROM master.dbo.syslogins   
    WHERE name IN('sysadmin', 'serveradmin','setupadmin', 'securityadmin','processadmin', 'dbcreator','diskadmin','bulkadmin')  
    ```  
  
2.  Löschen Sie die Anmeldungen.  
  
3.  Verwenden der **Sp_addlogin** Prozedur zum Erstellen neuer Anmeldungen. Gibt an, die SID zurückgegeben wird, in Schritt 1 der **@sid** Parameter für die jeweilige Anmeldung.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
