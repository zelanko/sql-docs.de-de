---
title: Konfigurieren von Parametern für die Datensammlung (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b9cdabe3a74570c44eba952137d6b9efb856a731
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62918562"
---
# <a name="configure-data-collection-parameters-transact-sql"></a>Konfigurieren von Parametern für die Datensammlung (Transact-SQL)
  Bevor Sie einen benutzerdefinierten Sammlungssatz erstellen, müssen Sie zuerst Datensammlungsparameter konfigurieren. Hierfür können Sie die gespeicherten Prozeduren verwenden, die mit dem Datensammler bereitgestellt werden. Um diese Aufgabe auszuführen, müssen Sie mit dem Abfrage-Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] den folgenden Vorgang durchführen.  
  
> [!NOTE]  
>  Parameter für die Datensammlung können nur einmal konfiguriert werden. Nach der Konfiguration werden diese Parameter für alle zusätzlichen Sammlungssätze verwendet, die Sie erstellen.  
  
### <a name="configure-data-collection-parameters"></a>Konfigurieren von Parametern für die Datensammlung  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit der Datenbank her, in der Sie einen benutzerdefinierten Sammlungssatz erstellen möchten.  
  
2.  Führen Sie im Abfrage-Editor die folgenden Anweisungen aus.  
  
    ```sql  
    USE msdb;  
    EXEC sp_syscollector_set_warehouse_instance_name N'INSTANCE_NAME';-- where instance name is the name of the SQL Server instance  
    EXEC sp_syscollector_set_warehouse_database_name N'MDW';  
    EXEC sp_syscollector_set_cache_directory N'D:\tempdata';  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datensammlung](data-collection.md)   
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql)  
  
  
