---
description: MSSQLSERVER_3961
title: MSSQLSERVER_3961 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3961 (Database Engine error)
ms.assetid: 3bbc6965-6445-400c-940a-2d85b037513f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 837215560e15ff01a84f614ac087ff96930db3cf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456128"
---
# <a name="mssqlserver_3961"></a>MSSQLSERVER_3961
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|3961|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|XACT_METADATA_INVALID|  
|Meldungstext|Fehler bei der Momentaufnahmeisolationstransaktion in der '%.*ls'-Datenbank, weil das von der Anweisung zugegriffene Objekt durch eine DDL-Anweisung in einer anderen gleichzeitigen Transaktion seit dem Beginn dieser Transaktion geändert wurde.  Der Vorgang ist nicht zulässig, weil für die Metadaten keine Versionsverwaltung durchgeführt wird. Ein gleichzeitiges Update von Metadaten kann zu Inkonsistenz führen, wenn es zu einer Vermischung mit der Momentaufnahmeisolation kommt.|  
  
## <a name="explanation"></a>Erklärung  
Dieser Fehler kann auftreten, wenn Sie im Rahmen der Momentaufnahmeisolation Metadaten abfragen und eine gleichzeitige DDL-Anweisung zum Aktualisieren der Metadaten vorhanden ist, auf die unter der Momentaufnahmeisolation zugegriffen wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt keine Versionsverwaltung von Metadaten. Aus diesem Grund gelten Einschränkungen dafür, welche DDL-Vorgänge innerhalb einer expliziten Transaktion durchgeführt werden können, die der Momentaufnahmeisolation unterliegen. Eine implizite Transaktion ist laut Definition eine einzelne Anweisung, mit der die Semantik der Momentaufnahmeisolation auch bei Verwendung von DDL-Anweisungen erzwungen werden kann. Die folgenden DDL-Anweisungen sind bei der Momentaufnahme-Isolationsstufe nach einer BEGIN TRANSACTION-Anweisung nicht zulässig: ALTER TABLE, CREATE INDEX, CREATE XML INDEX, ALTER INDEX, DROP INDEX, DBCC REINDEX, ALTER PARTITION FUNCTION, ALTER PARTITION SCHEME oder eine beliebige CLR-DDL-Anweisung (Common Language Runtime). Diese Anweisungen sind zulässig, wenn Sie die Momentaufnahmeisolation in impliziten Transaktionen verwenden. Eine implizite Transaktion ist laut Definition eine einzelne Anweisung, mit der die Semantik der Momentaufnahmeisolation auch bei Verwendung von DDL-Anweisungen erzwungen werden kann.  
  
## <a name="user-action"></a>Benutzeraktion  
Ändern Sie die Momentaufnahmeisolationsstufe vor dem Abfragen von Metadaten in eine Isolationsstufe, bei der es sich nicht um eine Momentaufnahmeisolationsstufe handelt, z. B. Read Committed.  
  
