---
title: Verwenden nicht gruppierter columnstore-Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 4c341fb8-7cb1-4cab-921b-e80b751d6c19
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c876eb6fdd466349ac369dcff8e292bc0839c669
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84927771"
---
# <a name="using-nonclustered-columnstore-indexes"></a>Verwenden nicht gruppierter Columnstore-Indizes
  Beschreibt wichtige Aufgaben für die Verwendung eines nicht gruppierten Columnstore-Indexes für eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Tabelle.

 Eine Übersicht über Columnstore-Indizes finden Sie unter [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).

 Informationen zum Verwenden von gruppierten Columnstore-Indizes finden Sie unter [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).

## <a name="contents"></a>Inhalte

-   [Erstellen eines nicht gruppierten Columnstore-Indexes](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#load)

-   [Ändern der Daten in einem nicht gruppierten Columnstore-Index](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#change)

##  <a name="create-a-nonclustered-columnstore-index"></a><a name="load"></a>Erstellen eines nicht gruppierten columnstore-Indexes
 Zum Laden von Daten in einen nicht gruppierten columnstore--Index laden Sie zuerst Daten in eine herkömmliche rowstore-Tabelle, die als Heap oder gruppierter Index gespeichert ist, und verwenden Sie dann [Create columnstore-Index &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql) , um einen columnstore--Index zu erstellen.

 ![Laden von Daten in einen columnstore-Index](../../2014/database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "Laden von Daten in einen columnstore-Index")

##  <a name="change-the-data-in-a-nonclustered-columnstore-index"></a><a name="change"></a>Ändern der Daten in einem nicht gruppierten columnstore-Index
 Wenn Sie einen nicht gruppierten Columnstore-Index für eine Tabelle erstellen, können Sie die Daten in dieser Tabelle nicht mehr direkt ändern. Eine Abfrage mit INSERT, UPDATE, MERGE oder DELETE schlägt fehl und gibt eine Fehlermeldung zurück. Um Daten in der Tabelle hinzuzufügen oder zu ändern, können Sie eine der folgenden Aktionen ausführen:

-   Deaktivieren Sie den columnstore--Index. Anschließend können Sie die Daten in der Tabelle aktualisieren. Wenn Sie den Columnstore-Index deaktivieren, können Sie den Columnstore-Index nach dem Aktualisieren der Daten neu erstellen. Beispiel:

    ```
    ALTER INDEX mycolumnstoreindex ON mytable DISABLE;
    -- update mytable --
    ALTER INDEX mycolumnstoreindex on mytable REBUILD
    ```

-   Löschen Sie den columnstore--Index, aktualisieren Sie die Tabelle, und erstellen Sie dann den columnstore--Index mit CREATE columnstore-Index neu. Beispiel:

    ```
    DROP INDEX mycolumnstoreindex ON mytable
    -- update mytable --
    CREATE NONCLUSTERED COLUMNSTORE INDEX mycolumnstoreindex ON mytable;

    ```

-   Laden Sie Daten in eine Stagingtabelle ohne Columnstore-Index. Erstellen Sie einen Columnstore-Index für die Stagingtabelle. Wechseln Sie für die Stagingtabelle in eine leere Partition der Haupttabelle.

-   Wechseln Sie für eine Partition in der Tabelle mit dem Columnstore-Index in eine leere Stagingtabelle. Wenn die Stagingtabelle über einen Columnstore-Index verfügt, deaktivieren Sie den Columnstore-Index. Nehmen Sie die gewünschten Updates vor. Erstellen bzw. erstellen Sie den Columnstore-Index neu. Wechseln Sie für die Stagingtabelle zurück in die (nun leere) Partition der Haupttabelle.




