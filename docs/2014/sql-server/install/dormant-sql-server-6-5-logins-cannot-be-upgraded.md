---
title: Ruhende SQL Server 6,5-Anmeldungen können nicht aktualisiert werden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- passwords [SQL Server], dormant logins
- dormant logins
- logins [SQL Server], upgrading dormant logins
- identifying dormant logins
- password hashes [SQL Server]
ms.assetid: ebe18a74-0375-4df4-b894-239f8fdabb64
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f78bca9bf2b99b2ab6f530613b64bc0e46c4001c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054815"
---
# <a name="dormant-sql-server-65-logins-cannot-be-upgraded"></a>Ein Upgrade ruhender SQL Server 6.5-Anmeldungen kann nicht durchgeführt werden
  Upgrade Advisor hat eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung erkannt, deren Kennwort nicht direkt auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] aktualisiert werden kann.  
  
 Sie müssen das entsprechende Kennwort neu festlegen, um diese Anmeldung zu aktivieren. Sie können das Kennwort mithilfe von ALTER LOGIN neu festlegen:  
  
```  
ALTER LOGIN <login name> WITH PASSWORD = '<new password>' MUST_CHANGE  
```  
  
 Das neue Kennwort wird auf die Erfüllung der Richtlinie für die Kennwortkomplexität Ihres Systems überprüft, es sei denn, die Richtlinienüberprüfung ist deaktiviert. Es wird empfohlen, komplexe Kennwörter zu verwenden und die Richtlinienüberprüfung nicht zu deaktivieren. Durch die Option MUST_CHANGE wird der Benutzer zum Auswählen eines neuen Kennworts gezwungen. Dies wird empfohlen, ist aber nicht erforderlich.  
  
 Sie können ruhende Anmeldungen mithilfe der folgenden Abfrage identifizieren:  
  
```  
SELECT * FROM sysxlogins WHERE (xstatus & 2048) = 2048;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
