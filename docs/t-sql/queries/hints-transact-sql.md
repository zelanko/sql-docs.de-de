---
title: Hinweise (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 7ee01e23c544ac01ee9fb85e5b59d31b73088987
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731295"
---
# <a name="hints-transact-sql"></a>Hinweise (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Hinweise sind Optionen oder Strategien, die angegeben werden, um bei Bedarf durch den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abfrageoptimierer für SELECT-, INSERT-, UPDATE- oder DELETE-Anweisungen erzwungen werden zu können. Diese Hinweise überschreiben jeden Ausführungsplan, den der Abfrageoptimierer möglicherweise für eine Abfrage auswählt.  
  
> [!CAUTION]  
>  Da der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abfrageoptimierer in der Regel den optimalen Ausführungsplan für eine Abfrage auswählt, wird empfohlen, dass erfahrene Entwickler und Datenbankadministratoren \<join_hint>, \<query_hint> und \<table_hint> nur dann verwenden, wenn alle anderen Möglichkeiten sich als unzureichend erwiesen haben.
  
 In diesem Abschnitt werden die folgenden Hinweise beschrieben:  
  
-   [Joinhinweise](../../t-sql/queries/hints-transact-sql-join.md)  
  
-   [Abfragehinweise](../../t-sql/queries/hints-transact-sql-query.md)  
  
-   [Tabellenhinweis](../../t-sql/queries/hints-transact-sql-table.md)  
  
  
