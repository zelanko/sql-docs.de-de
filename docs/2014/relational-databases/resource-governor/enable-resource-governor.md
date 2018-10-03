---
title: Aktivieren der Ressourcenkontrolle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, enabling
ms.assetid: 4d17af53-cf11-4ce4-aab4-deda94a49836
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6e3d6ee852f6631014a4407e09f7b41646e9f9cb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48214550"
---
# <a name="enable-resource-governor"></a>Aktivieren der Ressourcenkontrolle
  Die Ressourcenkontrolle ist standardmäßig deaktiviert. Sie können die Ressourcenkontrolle in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder mit Transact-SQL aktivieren.  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **So aktivieren Sie den Resource Governor über:**  [Objekt-Explorer](#RGOnObjEx), [Eigenschaften des Resource Governor](#RGOnProp), [Transact-SQL](#RGOnTSQL)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
 Wenn Sie die Ressourcenkontrolle aktivieren, geschieht Folgendes:  
  
-   Die Klassifizierungsfunktion wird für neue Verbindungen ausgeführt, damit deren Arbeitsauslastungen Arbeitsauslastungsgruppen zugeordnet werden können.  
  
-   Die in der Konfiguration der Ressourcenkontrolle angegebenen Ressourcengrenzwerte werden überprüft und durchgesetzt.  
  
-   Alle Konfigurationsänderungen, die bei deaktivierter Ressourcenkontrolle vorgenommen wurden, wirken sich auf Anforderungen aus, die bereits bestanden, bevor die Ressourcenkontrolle aktiviert wurde.  
  
###  <a name="LimitationsRestrictions"></a> Einschränkungen  
 Mithilfe der `ALTER RESOURCE GOVERNOR`-Anweisung können Sie die Ressourcenkontrolle während einer Benutzertransaktion nicht aktivieren.  
  
###  <a name="Permissions"></a> Berechtigungen  
 Zum Aktivieren der Ressourcenkontrolle ist die CONTROL SERVER-Berechtigung erforderlich.  
  
##  <a name="RGOnObjEx"></a> Aktivieren der Ressourcenkontrolle im Objekt-Explorer  
 **So aktivieren Sie die Ressourcenkontrolle im Objekt-Explorer**  
  
1.  Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]den Objekt-Explorer, und erweitern Sie den Knoten **Verwaltung** rekursiv, bis **Ressourcenkontrolle**angezeigt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf den **Resource Governor**, und klicken Sie anschließend auf **Aktivieren**.  
  
##  <a name="RGOnProp"></a> Aktivieren der Ressourcenkontrolle über die Eigenschaften der Ressourcenkontrolle  
 **So aktivieren Sie die Ressourcenkontrolle auf der Eigenschaftenseite der Ressourcenkontrolle**  
  
1.  Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]den Objekt-Explorer, und erweitern Sie den Knoten **Verwaltung** rekursiv, bis **Ressourcenkontrolle**angezeigt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Resource Governor** , und klicken Sie dann auf **Eigenschaften**. Damit öffnen Sie die Seite **Eigenschaften der Resource Governor** .  
  
3.  Aktivieren Sie das Kontrollkästchen **Ressourcenkontrolle aktivieren** , und klicken Sie dann auf **OK**.  
  
##  <a name="RGOnTSQL"></a> Aktivieren der Ressourcenkontrolle mit Transact-SQL  
 **So aktivieren Sie die Ressourcenkontrolle mit Transact-SQL**  
  
1.  Führen Sie die **ALTER RESOURCE GOVERNOR RECONFIGURE** -Anweisung aus.  
  
### <a name="example-transact-sql"></a>Beispiel (Transact-SQL)  
 Im folgenden Beispiel wird die Ressourcenkontrolle aktiviert.  
  
```  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Resource Governor](resource-governor.md)   
 [Deaktivieren der Ressourcenkontrolle](disable-resource-governor.md)   
 [Ressourcenpool für die Ressourcenkontrolle](resource-governor-resource-pool.md)   
 [Arbeitsauslastungsgruppe der Ressourcenkontrolle](resource-governor-workload-group.md)   
 [Klassifizierungsfunktion der Ressourcenkontrolle](resource-governor-classifier-function.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
