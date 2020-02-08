---
title: Erstellen eines Ressourcenpools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- resource pools [SQL Server], create
- Resource Governor, resource pool create
ms.assetid: 44dd0567-a4c8-4c72-89ff-e76f6ddef344
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 07c1743107d3edce7012740a3f1600d2157bf001
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68136886"
---
# <a name="create-a-resource-pool"></a>Erstellen eines Ressourcenpools
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]können Sie einen Ressourcenpool erstellen. Informationen zu den Grundlagen von Ressourcenpools finden Sie unter [Resource Governor Resource Pool](../../relational-databases/resource-governor/resource-governor-resource-pool.md).  
  
-   **Vorbereitungen:**  [Begrenzungen und Einschränkungen](#LimitationsRestrictions), [Berechtigungen](#Permissions)  
  
-   **So erstellen Sie einen Ressourcenpool mit:**  [SQL Server Management Studio](#CreRPProp), [Transact-SQL](#CreRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="LimitationsRestrictions"></a> Einschränkungen  
 Der maximale CPU-Prozentsatz muss gleich oder höher als der minimale CPU-Prozentsatz sein. Der maximale Arbeitsspeicherprozentsatz muss gleich oder höher als der minimale Arbeitsspeicherprozentsatz sein.  
  
 Die Summe der minimalen CPU-Prozentsätze und minimalen Arbeitsspeicherprozentsätze für alle Ressourcenpools darf nicht größer als 100 sein.  
  
###  <a name="Permissions"></a> Berechtigungen  
 Zum Erstellen eines Ressourcenpools ist die CONTROL SERVER-Berechtigung erforderlich.  
  
##  <a name="CreRPProp"></a> Erstellen eines Ressourcenpools in SQL Server Management Studio  
 **So erstellen Sie einen Ressourcenpool in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]den Objekt-Explorer, und erweitern Sie den Knoten **Verwaltung** rekursiv, bis **Ressourcenkontrolle**angezeigt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Resource Governor**, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Klicken Sie im Raster **Ressourcenpools** auf die erste Spalte in der leeren Zeile. Diese Spalte weist ein Sternchen (*) auf.  
  
4.  Doppelklicken Sie auf die leere Zelle in der Spalte **Name** . Geben Sie den gewünschten Namen für den Ressourcenpool ein.  
  
5.  Klicken oder doppelklicken Sie auf beliebige Zellen in der Zeile, die Sie sich ändern möchten, und geben Sie die neuen Werte ein.  
  
6.  Klicken Sie auf **OK**, um die Änderungen zu speichern.  
  
##  <a name="CreRPTSQL"></a> Erstellen eines Ressourcenpools mit Transact-SQL  
 **So erstellen Sie einen Ressourcenpool in [!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
1.  Führen Sie die [CREATE RESOURCE POOL](../../t-sql/statements/create-resource-pool-transact-sql.md) - oder die [CREATE EXTERNAL RESOURCE POOL](../../t-sql/statements/create-external-resource-pool-transact-sql.md) -Anweisung aus und geben Sie dabei die festzulegenden Eigenschaftswerte an.  
  
2.  Führen Sie die **ALTER RESOURCE GOVERNOR RECONFIGURE** -Anweisung aus.  
  
### <a name="example-transact-sql"></a>Beispiel (Transact-SQL)  
 Im folgenden Beispiel wird ein Ressourcenpool mit dem Namen `poolAdhoc`erstellt.  
  
```  
CREATE RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 20);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Aktivieren der Ressourcenkontrolle](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [Ressourcenpool für die Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Ändern der Einstellungen für den Ressourcenpool](../../relational-databases/resource-governor/change-resource-pool-settings.md)   
 [Löschen eines Ressourcenpools](../../relational-databases/resource-governor/delete-a-resource-pool.md)   
 [Konfigurieren der Ressourcenkontrolle mit einer Vorlage](../../relational-databases/resource-governor/configure-resource-governor-using-a-template.md)   
 [Arbeitsauslastungsgruppe der Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Klassifizierungsfunktion der Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)  
  
  
