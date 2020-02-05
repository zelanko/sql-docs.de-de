---
title: MSSQLSERVER_12329 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 12329 (Database Engine error)
ms.assetid: 43f90287-36d5-46c2-ac91-a37202dcf6d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 404f414a1f4bfe75c3476e0954e810c4b36ddaa3
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68002900"
---
# <a name="mssqlserver_12329"></a>MSSQLSERVER_12329
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|12329|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|HK_UNSUPPORTED_NON_LATIN_CODEPAGE|  
|Meldungstext|Die Datentypen char(n) und varchar(n), die Sortierungen mit einer anderen Codepage als 1252 verwenden, werden bei *construct* nicht unterstützt.|  
  
## <a name="explanation"></a>Erklärung  
Verwenden Sie die Datentypen char(n) und varchar(n) nicht mit Sortierungen, die eine andere Codepage als 1252 verwenden.  
  
## <a name="user-action"></a>Benutzeraktion  
Die folgende unerwartete Situation kann zu diesem Fehler führen:  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = 'us_english')  
```  
  
Verwenden Sie stattdessen:  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
```  
  
