---
title: Ändern eines Indexes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], modifying
- modifying indexes
- index changes [SQL Server]
ms.assetid: 97e3110d-fde7-4f5d-9309-dc1697960aeb
caps.latest.revision: 18
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a34096c26200a2defbb8cac28f685fba9ac37fcc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152371"
---
# <a name="modify-an-index"></a>Ändern eines Indexes
  In diesem Thema wird beschrieben, wie Sie einen Index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]ändern.  
  
> [!IMPORTANT]  
>  Indizes, die als Ergebnis einer PRIMARY KEY- oder UNIQUE-Einschränkung erstellt wurden, können mit dieser Methode nicht geändert werden. In diesem Fall muss die Einschränkung geändert werden.  
  
 **In diesem Thema**  
  
-   **Ändern eines Indexes mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-modify-an-index"></a>So ändern Sie einen Index  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**und dann die Datenbank, zu der die Tabelle gehört, und klicken Sie anschließend auf **Tabellen**.  
  
3.  Erweitern Sie die Tabelle, in die der Index gehört, und erweitern Sie dann **Indizes**.  
  
4.  Klicken Sie mit der rechten Maustaste auf den Index, den Sie ändern möchten, und klicken Sie dann auf **Eigenschaften**.  
  
5.  Nehmen Sie im Dialogfeld **Indexeigenschaften** die gewünschten Änderungen vor. Sie können z. B. eine Spalte im Indexschlüssel hinzufügen oder entfernen oder die Einstellung einer Indexoption ändern.  
  
#### <a name="to-modify-index-columns"></a>So ändern Sie Indexspalten  
  
1.  Wenn Sie die Position einer Indexspalte hinzufügen, entfernen oder ändern möchten, wählen Sie im Dialogfeld **Indexeigenschaften** die Seite **Allgemein** aus.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-modify-an-index"></a>So ändern Sie einen Index  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird ein vorhandener Index für die `ProductID` -Spalte der `Production.WorkOrder` -Tabelle mithilfe der `DROP_EXISTING` -Option gelöscht und neu erstellt. Die Optionen `FILLFACTOR` und `PAD_INDEX` sind ebenfalls festgelegt.  
  
     [!code-sql[IndexDDL#CreateIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/createindex.sql#createindex4)]  
  
     Im folgenden Beispiel werden mithilfe von ALTER INDEX mehrere Optionen für den `AK_SalesOrderHeader_SalesOrderNumber`-Index festgelegt.  
  
     [!code-sql[IndexDDL#AlterIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex4)]  
  
#### <a name="to-modify-index-columns"></a>So ändern Sie Indexspalten  
  
1.  Wenn Sie die Position einer Indexspalte hinzufügen, entfernen oder ändern möchten, müssen Sie den Index löschen und neu erstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [INDEXPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql)   
 [sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)   
 [sys.index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql)   
 [Festlegen von Indexoptionen](set-index-options.md)   
 [Umbenennen von Indizes](indexes.md)  
  
  
