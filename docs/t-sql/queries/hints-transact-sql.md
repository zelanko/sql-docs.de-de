---
description: Hinweise (Transact-SQL)
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
ms.openlocfilehash: 16f0e437e864ccb2bd0b4c173b40d84098c51b30
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88459184"
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
  
  
