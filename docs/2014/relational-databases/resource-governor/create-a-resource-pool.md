---
title: Erstellen eines Ressourcenpools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- resource pools [SQL Server], create
- Resource Governor, resource pool create
ms.assetid: 44dd0567-a4c8-4c72-89ff-e76f6ddef344
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5abd2e60f4f9bb5290b47f95349782f8b26ad8bb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85043201"
---
# <a name="create-a-resource-pool"></a>Erstellen eines Ressourcenpools
  Mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]können Sie einen Ressourcenpool erstellen.  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **Zum Erstellen eines Ressourcenpools mit:**  [SQL Server Management Studio](#CreRPProp), [Transact-SQL](#CreRPTSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Einschränkungen  
 Der maximale CPU-Prozentsatz muss gleich oder höher als der minimale CPU-Prozentsatz sein. Der maximale Arbeitsspeicherprozentsatz muss gleich oder höher als der minimale Arbeitsspeicherprozentsatz sein.  
  
 Die Summe der minimalen CPU-Prozentsätze und minimalen Arbeitsspeicherprozentsätze für alle Ressourcenpools darf nicht größer als 100 sein.  
  
###  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Zum Erstellen eines Ressourcenpools ist die CONTROL SERVER-Berechtigung erforderlich.  
  
##  <a name="create-a-resource-pool-using-sql-server-management-studio"></a><a name="CreRPProp"></a> Erstellen eines Ressourcenpools in SQL Server Management Studio  
 **So erstellen Sie einen Ressourcenpool in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]den Objekt-Explorer, und erweitern Sie den Knoten **Verwaltung** rekursiv, bis **Ressourcenkontrolle**angezeigt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Resource Governor**, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Klicken Sie im Raster **Ressourcenpools** auf die erste Spalte in der leeren Zeile. Diese Spalte weist ein Sternchen (*) auf.  
  
4.  Doppelklicken Sie auf die leere Zelle in der Spalte **Name** . Geben Sie den gewünschten Namen für den Ressourcenpool ein.  
  
5.  Klicken oder doppelklicken Sie auf beliebige Zellen in der Zeile, die Sie sich ändern möchten, und geben Sie die neuen Werte ein.  
  
6.  Klicken Sie auf **OK**, um die Änderungen zu speichern.  
  
##  <a name="create-a-resource-pool-using-transact-sql"></a><a name="CreRPTSQL"></a>Erstellen eines Ressourcenpools mit Transact-SQL  
 **So erstellen Sie einen Ressourcenpool in [!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
1.  Führen Sie die `CREATE RESOURCE POOL`-Anweisung aus, und geben Sie dabei die festzulegenden Eigenschaftswerte an.  
  
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
 [Resource Governor](resource-governor.md)   
 [Aktivieren der Ressourcenkontrolle](enable-resource-governor.md)   
 [Ressourcenpool für die Ressourcenkontrolle](resource-governor-resource-pool.md)   
 [Ändern der Einstellungen für den Ressourcen Pool](change-resource-pool-settings.md)   
 [Löschen eines Ressourcenpools](delete-a-resource-pool.md)   
 [Konfigurieren der Ressourcenkontrolle mit einer Vorlage](configure-resource-governor-using-a-template.md)   
 [Arbeitsauslastungsgruppe der Ressourcenkontrolle](resource-governor-workload-group.md)   
 [Resource Governor Classifier-Funktion](resource-governor-classifier-function.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
