---
title: Verwendung von nicht gruppierten columnstore-Indizes | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-indexes
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4c341fb8-7cb1-4cab-921b-e80b751d6c19
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.openlocfilehash: fd711b644c551da7a658eff7ede74007d69a2286
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059199"
---
# <a name="using-nonclustered-columnstore-indexes"></a>Verwenden nicht gruppierter Columnstore-Indizes
  Beschreibt wichtige Aufgaben für die Verwendung eines nicht gruppierten Columnstore-Indexes für eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Tabelle.  
  
 Einen Überblick über die columnstore-Indizes finden Sie unter [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).  
  
 Weitere Informationen zu gruppierten columnstore-Indizes finden Sie unter [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).  
  
## <a name="contents"></a>Inhalt  
  
-   [Erstellen Sie einen nicht gruppierten columnstore-Index](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#load)  
  
-   [Ändern Sie die Daten in einem nicht gruppierten columnstore-Index](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#change)  
  
##  <a name="load"></a> Erstellen Sie einen nicht gruppierten columnstore-Index  
 Um Daten in einen nicht gruppierten columnstore-Index zuladen, laden Sie zuerst Daten in eine herkömmliche Rowstore-Tabelle gespeichert, die als Heap oder gruppierten index, und verwenden [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-columnstore-index-transact-sql) zum Erstellen einer columnstore-Index.  
  
 ![Laden von Daten in einen columnstore-Index](../../2014/database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "Laden von Daten in einen columnstore-Index")  
  
##  <a name="change"></a> Ändern Sie die Daten in einem nicht gruppierten columnstore-Index  
 Wenn Sie einen nicht gruppierten Columnstore-Index für eine Tabelle erstellen, können Sie die Daten in dieser Tabelle nicht mehr direkt ändern. Eine Abfrage mit INSERT, UPDATE, MERGE oder DELETE schlägt fehl und gibt eine Fehlermeldung zurück. Um Daten in der Tabelle hinzuzufügen oder zu ändern, können Sie eine der folgenden Aktionen ausführen:  
  
-   Deaktivieren Sie den columnstore-Index. Anschließend können Sie die Daten in der Tabelle aktualisieren. Wenn Sie den Columnstore-Index deaktivieren, können Sie den Columnstore-Index nach dem Aktualisieren der Daten neu erstellen. Zum Beispiel:  
  
    ```  
    ALTER INDEX mycolumnstoreindex ON mytable DISABLE;  
    -- update mytable --  
    ALTER INDEX mycolumnstoreindex on mytable REBUILD  
    ```  
  
-   Löschen Sie den columnstore-Index, aktualisiert die Tabelle, und klicken Sie dann den columnstore-Index mit CREATE COLUMNSTORE INDEX neu erstellen. Zum Beispiel:  
  
    ```  
    DROP INDEX mycolumnstoreindex ON mytable  
    -- update mytable --  
    CREATE NONCLUSTERED COLUMNSTORE INDEX mycolumnstoreindex ON mytable;  
  
    ```  
  
-   Laden Sie Daten in eine Stagingtabelle ohne Columnstore-Index. Erstellen Sie einen Columnstore-Index für die Stagingtabelle. Wechseln Sie für die Stagingtabelle in eine leere Partition der Haupttabelle.  
  
-   Wechseln Sie für eine Partition in der Tabelle mit dem Columnstore-Index in eine leere Stagingtabelle. Wenn die Stagingtabelle über einen Columnstore-Index verfügt, deaktivieren Sie den Columnstore-Index. Nehmen Sie die gewünschten Updates vor. Erstellen bzw. erstellen Sie den Columnstore-Index neu. Wechseln Sie für die Stagingtabelle zurück in die (nun leere) Partition der Haupttabelle.  
  

  
  
