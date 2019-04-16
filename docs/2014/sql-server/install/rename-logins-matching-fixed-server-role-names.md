---
title: Umbenennen von Anmeldungen, die mit Namen fester Serverrollen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- user-defined login names [SQL Server]
- fixed server roles [SQL Server]
- renamed logins [SQL Server]
- logins [SQL Server], names
ms.assetid: 10a1d77c-3153-474f-a6a0-969556794467
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fa2e74dfc1afdfe25058657d910315a3fb626f1c
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582075"
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
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
