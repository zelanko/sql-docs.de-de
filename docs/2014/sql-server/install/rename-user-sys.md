---
title: Umbenennen von Benutzer ' sys ' | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- sys user names [SQL Server]
ms.assetid: d622d646-83e4-4b6f-9a21-77b301af04b5
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ddcadb1fe32c61fbab45bbdcfbc18d60d1072d23
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48078213"
---
# <a name="rename-user-sys"></a>Benennen Sie den Benutzer 'sys' um
  Upgrade Advisor hat erkannt, der Benutzername **Sys** in einer Datenbank. Dieser Name ist reserviert. Benennen Sie den Benutzer um, bevor Sie ein Upgrade durchführen. Wenn der Benutzer nicht umbenannt wird, ist die Datenbank nach dem Upgradevorgang fehlerverdächtig und nicht verfügbar, bis die Datenbank online geschaltet wird.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Benutzer **Sys** ist reserviert.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
  
### <a name="before-upgrade-procedure"></a>Vorgehensweise vor dem Upgrade  
 Bevor Sie, in jeder Datenbank aktualisieren, die Benutzer enthält **Sys**, gehen Sie folgendermaßen vor:  
  
1.  Erstellen Sie einen neuen Benutzer.  
  
2.  Verwenden Sie die folgenden Anweisungen alle Berechtigungen an, die vom Benutzer gewährt werden **Sys** und Benutzer erteilt **Sys**.  
  
    ```  
    -- Return permissions granted by user sys.  
    SELECT * FROM sysprotects WHERE grantor = USER_ID('sys')  
    -- Return permissions granted to user sys.  
    SELECT * FROM sysprotects WHERE uid = USER_ID('sys')  
    ```  
  
3.  Zum Übertragen des Besitzes aller Objekte, die im Besitz von **Sys** verwenden, um den neuen Benutzer **Sp_changeobjectowner**.  
  
4.  Löschen Sie den Benutzer **Sys**.  
  
5.  Um in Schritt 2 aufgezeichneten ursprünglichen Berechtigungen wiederherzustellen, verwenden Sie die AS *neues* -Klausel der GRANT-Anweisung.  
  
6.  Ändern Sie die Skripts so, dass sie auf den neuen Benutzer verweisen. So müssen z. B. Skripts, die Anweisungen wie `SELECT * FROM sys.my`_`table` enthalten, in `SELECT * FROM new_user.my_table` geändert werden.  
  
### <a name="after-upgrade-procedure"></a>Vorgehensweise nach dem Upgrade  
 Wenn der Benutzer **Sys** wurde vor dem Upgrade nicht umbenannt, gehen Sie folgendermaßen vor:  
  
1.  Führen Sie die Anweisung `ALTER DATABASE db_name SET ONLINE` aus. Die Datenbank befindet sich im SINGLE_USER-Modus.  
  
2.  Führen Sie alle Schritte im Abschnitt "Vorgehensweise vor dem Upgrade" aus.  
  
3.  Führen Sie die Anweisung `ALTER DATABASE db_name SET MULTI_USER` aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
