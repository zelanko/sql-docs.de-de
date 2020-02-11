---
title: Umbenennen von Benutzern in sys | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sys user names [SQL Server]
ms.assetid: d622d646-83e4-4b6f-9a21-77b301af04b5
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ce8656df63c9d415ca09b54ecb86b87aba8bd83a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66092861"
---
# <a name="rename-user-sys"></a>Benennen Sie den Benutzer 'sys' um
  Der Upgrade Advisor hat den Benutzernamen **sys** in einer Datenbank erkannt. Dieser Name ist reserviert. Benennen Sie den Benutzer um, bevor Sie ein Upgrade durchführen. Wenn der Benutzer nicht umbenannt wird, ist die Datenbank nach dem Upgradevorgang fehlerverdächtig und nicht verfügbar, bis die Datenbank online geschaltet wird.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Der Benutzer **sys** ist reserviert.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
  
### <a name="before-upgrade-procedure"></a>Vorgehensweise vor dem Upgrade  
 Führen Sie vor dem Upgrade in jeder Datenbank, die den Benutzer **sys**enthält, folgende Schritte aus:  
  
1.  Erstellen Sie einen neuen Benutzer.  
  
2.  Verwenden Sie die folgenden Anweisungen, um alle Berechtigungen anzuzeigen, die vom Benutzer **sys** erteilt und für den Benutzer **sys**erteilt wurden.  
  
    ```  
    -- Return permissions granted by user sys.  
    SELECT * FROM sysprotects WHERE grantor = USER_ID('sys')  
    -- Return permissions granted to user sys.  
    SELECT * FROM sysprotects WHERE uid = USER_ID('sys')  
    ```  
  
3.  Verwenden Sie **sp_changeobjectowner**, um den Besitz aller Objekte im Besitz von **sys** auf den neuen Benutzer zu übertragen.  
  
4.  Löschen Sie den Benutzer **sys**.  
  
5.  Verwenden Sie die as *new_user* -Klausel der GRANT-Anweisung, um die in Schritt 2 erfassten ursprünglichen Berechtigungen wiederherzustellen.  
  
6.  Ändern Sie die Skripts so, dass sie auf den neuen Benutzer verweisen. So müssen z. B. Skripts, die Anweisungen wie `SELECT * FROM sys.my`_`table` enthalten, in `SELECT * FROM new_user.my_table` geändert werden.  
  
### <a name="after-upgrade-procedure"></a>Vorgehensweise nach dem Upgrade  
 Wenn der Benutzer **sys** vor dem Upgrade nicht umbenannt wurde, gehen Sie wie folgt vor:  
  
1.  Führen Sie die Anweisung `ALTER DATABASE db_name SET ONLINE` aus. Die Datenbank befindet sich im SINGLE_USER-Modus.  
  
2.  Führen Sie alle Schritte im Abschnitt "Vorgehensweise vor dem Upgrade" aus.  
  
3.  Führen Sie die Anweisung `ALTER DATABASE db_name SET MULTI_USER` aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
