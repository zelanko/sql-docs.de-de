---
description: MSSQLSERVER_9001
title: MSSQLSERVER_9001 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9001 (Database Engine error)
ms.assetid: a54de936-90c6-4845-aa96-29d32f154601
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dcccb9a93c762cf7ccb1d690bc0894005dc30da3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494468"
---
# <a name="mssqlserver_9001"></a>MSSQLSERVER_9001
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|9001|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LOG_NOT_AVAIL|  
|Meldungstext|Das Protokoll für die '%.*ls'-Datenbank ist nicht verfügbar. Überprüfen Sie das Ereignisprotokoll auf verwandte Fehlermeldungen. Beheben Sie ggf. alle Fehler, und starten Sie die Datenbank neu.|  
  
## <a name="explanation"></a>Erklärung  
Das Datenbankprotokoll wurde offline geschaltet Normalerweise ist dies ein Zeichen für einen schwerwiegenden Fehle, der einen Neustart der Datenbank erfordert.  
  
## <a name="user-action"></a>Benutzeraktion  
Diagnostizieren Sie andere Fehler, und starten Sie die Instanz von SQL Server neu, wenn sie sich noch nicht selbst neu gestartet hat.  
  
