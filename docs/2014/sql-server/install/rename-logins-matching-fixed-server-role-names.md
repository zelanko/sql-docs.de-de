---
title: Umbenennen von Anmeldungen, die mit Namen fester Serverrollen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user-defined login names [SQL Server]
- fixed server roles [SQL Server]
- renamed logins [SQL Server]
- logins [SQL Server], names
ms.assetid: 10a1d77c-3153-474f-a6a0-969556794467
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 54223b28e681115df1b4ecf11f4fb96d13c68fd9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057738"
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
  
3.  Verwenden der **Sp_addlogin** Systemprozedur zum Erstellen neuer Anmeldungen. Geben Sie die SID in Schritt 1 zurückgegeben der **@sid** Parameter für die jeweilige Anmeldung.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
