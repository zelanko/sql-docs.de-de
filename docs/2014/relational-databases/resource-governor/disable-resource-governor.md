---
title: Deaktivieren der Ressourcenkontrolle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, disabling
ms.assetid: 2c2d2db0-34a5-4f50-b783-17693e3ce3f1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 75feaf114355c3a23abad6ec23be9011e0de5e06
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63209712"
---
# <a name="disable-resource-governor"></a>Deaktivieren der Ressourcenkontrolle
  Sie können die Ressourcenkontrolle in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder mit Transact-SQL deaktivieren.  
  
-   **Vorbereitungen:**  [Begrenzungen und Einschränkungen](#LimitationsRestrictions), [Berechtigungen](#Permissions)  
  
-   **So deaktivieren Sie den Resource Governor mit:**  [dem Objekt-Explorer](#RGOffObjEx), [Resource Governor-Eigenschaften](#RGOffProp), [Transact-SQL](#RGOffTSQL)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
 Wenn Sie die Ressourcenkontrolle deaktivieren, geschieht Folgendes:  
  
-   Die Klassifizierungsfunktion wird nicht ausgeführt.  
  
-   Alle neuen Verbindungen werden automatisch der Standardarbeitsauslastungsgruppe zugewiesen.  
  
-   Vom System initiierte Anforderungen werden der internen Arbeitsauslastungsgruppe zugewiesen.  
  
-   Alle Einstellungen für bestehende Arbeitsauslastungsgruppen und Ressourcenpools werden auf die Standardwerte zurückgesetzt. In diesem Fall werden keine Ereignisse ausgelöst, wenn Grenzwerte erreicht werden.  
  
-   Die reguläre Systemüberwachung bleibt unbeeinflusst.  
  
-   Sie können die Konfiguration ändern, die Änderungen treten jedoch erst in Kraft, wenn die Ressourcenkontrolle wieder aktiviert wird.  
  
-   Beim Neustart von SQL Server lädt die Ressourcenkontrolle nicht ihre Konfiguration, sondern enthält lediglich die Standardarbeitsauslastungsgruppen und -pools sowie die internen Gruppen und Ressourcenpools.  
  
###  <a name="LimitationsRestrictions"></a> Einschränkungen  
 Mithilfe der `ALTER RESOURCE GOVERNOR`-Anweisung können Sie die Ressourcenkontrolle während einer Benutzertransaktion nicht deaktivieren.  
  
###  <a name="Permissions"></a> Berechtigungen  
 Zum Deaktivieren der Ressourcenkontrolle ist die CONTROL SERVER-Berechtigung erforderlich.  
  
##  <a name="RGOffObjEx"></a> Deaktivieren der Ressourcenkontrolle im Objekt-Explorer  
 **So deaktivieren Sie die Ressourcenkontrolle im Objekt-Explorer**  
  
1.  Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]den Objekt-Explorer, und erweitern Sie den Knoten **Verwaltung** rekursiv, bis **Ressourcenkontrolle**angezeigt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Resource Governor**, und klicken Sie dann auf **Deaktivieren**.  
  
##  <a name="RGOffProp"></a> Deaktivieren der Ressourcenkontrolle über die Eigenschaften der Ressourcenkontrolle  
 **So deaktivieren Sie die Ressourcenkontrolle auf der Eigenschaftenseite der Ressourcenkontrolle**  
  
1.  Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]den Objekt-Explorer, und erweitern Sie den Knoten **Verwaltung** rekursiv, bis **Ressourcenkontrolle**angezeigt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Resource Governor** , und klicken Sie dann auf **Eigenschaften**. Damit öffnen Sie die Seite **Eigenschaften des Resource Governors** .  
  
3.  Aktivieren Sie das Kontrollkästchen **Ressourcenkontrolle aktivieren** , stellen Sie sicher, dass Kontrollkästchen nicht aktiviert ist, und klicken Sie dann auf **OK**.  
  
##  <a name="RGOffTSQL"></a> Deaktivieren der Ressourcenkontrolle mit Transact-SQL  
 **So deaktivieren Sie die Ressourcenkontrolle mit Transact-SQL**  
  
1.  Führen Sie die Anweisung **ALTER RESOURCE GOVERNOR DISABLE** aus.  
  
### <a name="example-transact-sql"></a>Beispiel (Transact-SQL)  
 Im folgenden Beispiel wird die Ressourcenkontrolle aktiviert.  
  
```  
ALTER RESOURCE GOVERNOR DISABLE;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Resource Governor](resource-governor.md)   
 [Aktivieren der Ressourcenkontrolle](enable-resource-governor.md)   
 [Ressourcenpool für die Ressourcenkontrolle](resource-governor-resource-pool.md)   
 [Arbeitsauslastungsgruppe der Ressourcenkontrolle](resource-governor-workload-group.md)   
 [Klassifizierungsfunktion der Ressourcenkontrolle](resource-governor-classifier-function.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
