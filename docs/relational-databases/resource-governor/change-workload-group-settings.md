---
title: Ändern der Einstellungen von Arbeitsauslastungsgruppen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- workload groups [SQL Server], alter
- Resource Governor, workload group alter
ms.assetid: 73b6109c-2ad0-4915-b11b-d40d5a0fdc25
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 99e93baf0ee07f7d60de147c90b52de9322b1805
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53380501"
---
# <a name="change-workload-group-settings"></a>Ändern der Einstellungen von Arbeitsauslastungsgruppen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]können Sie die Einstellungen von Arbeitsauslastungsgruppen ändern.  
  
-   **Vorbereitungen:**  [Begrenzungen und Einschränkungen](#LimitationsRestrictions), [Berechtigungen](#Permissions)  
  
-   **So ändern Sie die Einstellungen einer Workloadgruppe mit:**  [SQL Server Management Studio](#ChgWGProp), [Transact-SQL](#ChgWGTSQL)  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
###  <a name="LimitationsRestrictions"></a> Einschränkungen  
 Sie können die Einstellungen der Standardarbeitsauslastungsgruppe und von benutzerdefinierten Arbeitsauslastungsgruppen ändern.  
  
 **REQUEST_MAX_MEMORY_GRANT_PERCENT**  
  
 Der durch die Indexerstellung für eine nicht ausgerichtete partitionierte Tabelle belegte Arbeitsspeicher ist proportional zur Anzahl der beteiligten Partitionen. Wenn der insgesamt erforderliche Arbeitsspeicher die Grenze übersteigt, die pro Abfrage von der Arbeitsauslastungsgruppe festgelegt wurde (REQUEST_MAX_MEMORY_GRANT_PERCENT), kann bei dieser Indexerstellung ein Fehler auftreten. Da die Standardarbeitsauslastungsgruppe Abfragen zulässt, die die pro Abfrage festgelegte Grenze mit dem mindestens für eine Kompatibilität mit SQL Server 2005 erforderlichen Arbeitsspeicher übersteigen, können Benutzer dieselbe Indexerstellung in der Standardarbeitsauslastungsgruppe ausführen. Voraussetzung ist, dass der Standardressourcenpool über ausreichend Gesamtarbeitsspeicher verfügt, um eine solche Abfrage ausführen zu können.  
  
 Bei der Indexerstellung darf mehr Arbeitsbereichsspeicher verwendet werden, als ursprünglich zugewiesen, um eine bessere Leistung zu erzielen. Die Ressourcenkontrolle unterstützt diese besondere Behandlung, die ursprüngliche und alle weiteren Speicherzuweisungen werden jedoch durch die Einstellungen für Arbeitsauslastungsgruppe und Ressourcenpool begrenzt.  
  
###  <a name="Permissions"></a> Berechtigungen  
 Zum Ändern der Einstellungen von Arbeitsauslastungsgruppen ist die CONTROL SERVER-Berechtigung erforderlich.  
  
##  <a name="ChgWGProp"></a> Ändern der Einstellungen von Arbeitsauslastungsgruppen in SQL Server Management Studio  
 **So ändern Sie die Einstellungen von Arbeitsauslastungsgruppen in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  Erweitern Sie im Objekt-Explorer den Knoten **Verwaltung** rekursiv nach unten, bis einschließlich des Ordners **Arbeitsauslastungsgruppen** , der die zu ändernde Arbeitsauslastungsgruppe enthält.  
  
2.  Klicken Sie mit der rechten Maustaste auf die zu ändernde Arbeitsauslastungsgruppe, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Wählen Sie auf der Seite **Eigenschaften der Ressourcenkontrolle** die Zeile für die Arbeitsauslastungsgruppe im Raster **Arbeitsauslastungsgruppen für Ressourcenpool** aus, sofern diese nicht automatisch ausgewählt wurde.  
  
4.  Klicken oder doppelklicken Sie auf die Zellen in der zu ändernden Zeile, und geben Sie die neuen Werte ein.  
  
5.  Klicken Sie auf **OK**, um die Änderungen zu speichern.  
  
##  <a name="ChgWGTSQL"></a> Ändern der Einstellungen von Arbeitsauslastungsgruppen mit Transact-SQL  
 **So ändern Sie die Einstellungen von Arbeitsauslastungsgruppen mit Transact-SQL**  
  
1.  Führen Sie die ALTER WORKLOAD GROUP-Anweisung aus, und geben Sie dabei die zu ändernden Eigenschaftswerte an.  
  
2.  Führen Sie die ALTER RESOURCE GOVERNOR RECONFIGURE-Anweisung aus.  
  
### <a name="example-transact-sql"></a>Beispiel (Transact-SQL)  
 Im folgenden Beispiel wird die Einstellung für die maximale prozentuale Arbeitsspeicherzuweisung für die Arbeitsauslastungsgruppe `groupAdhoc`geändert.  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
WITH (REQUEST_MAX_MEMORY_GRANT_PERCENT = 30);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor.md)   
 [Erstellen einer Arbeitsauslastungsgruppe](../../relational-databases/resource-governor/create-a-workload-group.md)   
 [Erstellen eines Ressourcenpools](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [Ändern der Einstellungen für den Ressourcenpool](../../relational-databases/resource-governor/change-resource-pool-settings.md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
