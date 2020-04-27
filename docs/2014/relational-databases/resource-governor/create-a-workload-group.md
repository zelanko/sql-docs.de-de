---
title: Erstellen einer Arbeitsauslastungsgruppe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, workload group create
- workload groups [SQL Server], create
ms.assetid: 072868ec-ceff-4db6-941b-281af731a067
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1cd3b72418d0791d70d28d2dca0a434190a2d4a9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "68198926"
---
# <a name="create-a-workload-group"></a>Erstellen einer Arbeitsauslastungsgruppe
  Sie können Arbeitsauslastungsgruppen in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder mit [!INCLUDE[tsql](../../includes/tsql-md.md)]erstellen.  
  
-   **Vorbereitungen:**  [Begrenzungen und Einschränkungen](#LimitationsRestrictions), [Berechtigungen](#Permissions)  
  
-   **Erstellen einer Arbeitsauslastungsgruppe mit:**  [SQL Server Management Studio](#CreWGProp), [Transact-SQL](#CreWGTSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Einschränkungen  
 **REQUEST_MAX_MEMORY_GRANT_PERCENT**  
  
 Der durch die Indexerstellung für eine nicht ausgerichtete partitionierte Tabelle belegte Arbeitsspeicher ist proportional zur Anzahl der beteiligten Partitionen. Wenn der insgesamt erforderliche Arbeitsspeicher die Grenze übersteigt, die pro Abfrage von der Arbeitsauslastungsgruppe festgelegt wurde (REQUEST_MAX_MEMORY_GRANT_PERCENT), kann bei dieser Indexerstellung ein Fehler auftreten. Da die Standardarbeitsauslastungsgruppe Abfragen zulässt, die die pro Abfrage festgelegte Grenze mit dem mindestens für eine Kompatibilität mit SQL Server 2005 erforderlichen Arbeitsspeicher übersteigen, können Benutzer dieselbe Indexerstellung in der Standardarbeitsauslastungsgruppe ausführen. Voraussetzung ist, dass der Standardressourcenpool über ausreichend Gesamtarbeitsspeicher verfügt, um eine solche Abfrage ausführen zu können.  
  
 Bei der Indexerstellung darf mehr Arbeitsbereichsspeicher verwendet werden, als ursprünglich zugewiesen, um eine bessere Leistung zu erzielen. Die Ressourcenkontrolle unterstützt diese besondere Behandlung, die ursprüngliche und alle weiteren Speicherzuweisungen werden jedoch durch die Einstellungen für Arbeitsauslastungsgruppe und Ressourcenpool begrenzt.  
  
###  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Zum Erstellen einer Arbeitsauslastungsgruppe ist die CONTROL SERVER-Berechtigung erforderlich.  
  
##  <a name="create-a-workload-group-using-sql-server-management-studio"></a><a name="CreWGProp"></a> Erstellen einer Arbeitsauslastungsgruppe in SQL Server Management Studio  
 **So erstellen Sie Arbeitsauslastungsgruppen in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  Erweitern Sie im Objekt-Explorer rekursiv den Knoten **Verwaltung** , bis einschließlich zum Ressourcenpool mit der zu ändernden Arbeitsauslastungsgruppe.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Ordner **Arbeitsauslastungsgruppen** , und klicken Sie dann auf **Neue Arbeitsauslastungsgruppe**.  
  
3.  Stellen Sie im Raster **Ressourcenpools** sicher, dass der Ressourcenpool, dem Sie die Arbeitsauslastungsgruppe hinzufügen möchten, markiert ist.  
  
4.  Das Raster **Arbeitsauslastungsgruppen für Ressourcenpool** weist eine neue Zeile mit einem leeren Namen und Standardwerten in den anderen Spalten auf.  
  
5.  Klicken Sie auf die Zelle **Name** , und geben Sie einen Namen für die Arbeitsauslastungsgruppe ein.  
  
6.  Klicken oder doppelklicken Sie auf beliebige andere Zellen in der Zeile, deren Standardeinstellungen Sie aufheben möchten, und geben Sie jeweils die neuen Werte ein.  
  
7.  Klicken Sie auf **OK**, um die Änderungen zu speichern.  
  
##  <a name="create-a-workload-group-using-transact-sql"></a><a name="CreWGTSQL"></a> Erstellen einer Arbeitsauslastungsgruppe mit Transact-SQL  
 **So erstellen Sie Arbeitsauslastungsgruppen in [!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
1.  Führen Sie die CREATE WORKLOAD GROUP-Anweisung aus, und geben Sie dabei die festzulegenden Eigenschaftswerte an.  
  
2.  Führen Sie die ALTER RESOURCE GOVERNOR RECONFIGURE-Anweisung aus.  
  
### <a name="example-transact-sql"></a>Beispiel (Transact-SQL)  
 Im folgenden Beispiel wird im Ressourcenpool `groupAdhoc` die Arbeitsauslastungsgruppe `poolAdhoc`erstellt.  
  
```  
CREATE WORKLOAD GROUP groupAdhoc  
USING poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Resource Governor](resource-governor.md)   
 [Aktivieren der Ressourcenkontrolle](enable-resource-governor.md)   
 [Erstellen eines Ressourcenpools](create-a-resource-pool.md)   
 [Ändern der Einstellungen von Arbeitsauslastungsgruppen](change-workload-group-settings.md)   
 [Erstellen und Testen einer benutzerdefinierten Klassifizierungsfunktion](create-and-test-a-classifier-user-defined-function.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
