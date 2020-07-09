---
title: Aktivieren der Ressourcenkontrolle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, enabling
ms.assetid: 4d17af53-cf11-4ce4-aab4-deda94a49836
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: acb23caea9e74af5a1f25f8d6d2acab31fbeb39f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85720456"
---
# <a name="enable-resource-governor"></a>Aktivieren der Ressourcenkontrolle
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Die Ressourcenkontrolle ist standardmäßig deaktiviert. Sie können die Ressourcenkontrolle in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder mit Transact-SQL aktivieren.  
  
-   **Vorbereitungen:**  [Begrenzungen und Einschränkungen](#LimitationsRestrictions), [Berechtigungen](#Permissions)  
  
-   **So aktivieren Sie den Resource Governor mit:**  [dem Objekt-Explorer](#RGOnObjEx), [Resource Governor-Eigenschaften](#RGOnProp), [Transact-SQL](#RGOnTSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
 Wenn Sie die Ressourcenkontrolle aktivieren, geschieht Folgendes:  
  
-   Die Klassifizierungsfunktion wird für neue Verbindungen ausgeführt, damit deren Arbeitsauslastungen Arbeitsauslastungsgruppen zugeordnet werden können.  
  
-   Die in der Konfiguration der Ressourcenkontrolle angegebenen Ressourcengrenzwerte werden überprüft und durchgesetzt.  
  
-   Alle Konfigurationsänderungen, die bei deaktivierter Ressourcenkontrolle vorgenommen wurden, wirken sich auf Anforderungen aus, die bereits bestanden, bevor die Ressourcenkontrolle aktiviert wurde.  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Einschränkungen  
 Mithilfe der **ALTER RESOURCE GOVERNOR** -Anweisung können Sie die Ressourcenkontrolle während einer Benutzertransaktion nicht aktivieren.  
  
###  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Zum Aktivieren der Ressourcenkontrolle ist die CONTROL SERVER-Berechtigung erforderlich.  
  
##  <a name="enable-resource-governor-using-object-explorer"></a><a name="RGOnObjEx"></a> Aktivieren der Ressourcenkontrolle im Objekt-Explorer  
 **So aktivieren Sie die Ressourcenkontrolle im Objekt-Explorer**  
  
1.  Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]den Objekt-Explorer, und erweitern Sie den Knoten **Verwaltung** rekursiv, bis **Ressourcenkontrolle**angezeigt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf den **Resource Governor**, und klicken Sie anschließend auf **Aktivieren**.  
  
##  <a name="enable-resource-governor-using-resource-governor-properties"></a><a name="RGOnProp"></a> Aktivieren der Ressourcenkontrolle über die Eigenschaften der Ressourcenkontrolle  
 **So aktivieren Sie die Ressourcenkontrolle auf der Eigenschaftenseite der Ressourcenkontrolle**  
  
1.  Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]den Objekt-Explorer, und erweitern Sie den Knoten **Verwaltung** rekursiv, bis **Ressourcenkontrolle**angezeigt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Resource Governor** , und klicken Sie dann auf **Eigenschaften**. Damit öffnen Sie die Seite **Eigenschaften des Resource Governors** .  
  
3.  Aktivieren Sie das Kontrollkästchen **Ressourcenkontrolle aktivieren** , und klicken Sie dann auf **OK**.  
  
##  <a name="enable-resource-governor-using-transact-sql"></a><a name="RGOnTSQL"></a> Aktivieren der Ressourcenkontrolle mit Transact-SQL  
 **So aktivieren Sie die Ressourcenkontrolle mit Transact-SQL**  
  
1.  Führen Sie die **ALTER RESOURCE GOVERNOR RECONFIGURE** -Anweisung aus.  
  
### <a name="example-transact-sql"></a>Beispiel (Transact-SQL)  
 Im folgenden Beispiel wird die Ressourcenkontrolle aktiviert.  
  
```  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Deaktivieren der Ressourcenkontrolle](../../relational-databases/resource-governor/disable-resource-governor.md)   
 [Ressourcenpool für die Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Arbeitsauslastungsgruppe der Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Klassifizierungsfunktion der Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
