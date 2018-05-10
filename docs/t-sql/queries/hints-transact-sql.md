---
title: Hinweise (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|queries
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- query optimizer [SQL Server], hints
- hints [SQL Server], about hints
- SELECT statement [SQL Server], hints
- hints [SQL Server]
- INSERT statement [SQL Server], hints
- UPDATE statement [SQL Server], hints
- DELETE statement [SQL Server], hints
ms.assetid: 99412475-b0df-4264-9938-33a0b302b41a
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a404f015c177fe38985c07470645e9a16e2cb716
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="hints-transact-sql"></a>Hinweise (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Hinweise sind Optionen oder Strategien, die angegeben werden, um bei Bedarf durch den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abfrageoptimierer für SELECT-, INSERT-, UPDATE- oder DELETE-Anweisungen erzwungen werden zu können. Diese Hinweise überschreiben jeden Ausführungsplan, den der Abfrageoptimierer möglicherweise für eine Abfrage auswählt.  
  
> [!CAUTION]  
>  Da der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abfrageoptimierer in der Regel den optimalen Ausführungsplan für eine Abfrage auswählt, wird empfohlen, dass erfahrene Entwickler und Datenbankadministratoren \<join_hint>, \<query_hint> und \<table_hint> nur dann verwenden, wenn alle anderen Möglichkeiten sich als unbefriedigend erwiesen haben.
  
 In diesem Abschnitt werden die folgenden Hinweise beschrieben:  
  
-   [Joinhinweise](../../t-sql/queries/hints-transact-sql-join.md)  
  
-   [Abfragehinweise](../../t-sql/queries/hints-transact-sql-query.md)  
  
-   [Tabellenhinweis](../../t-sql/queries/hints-transact-sql-table.md)  
  
  
