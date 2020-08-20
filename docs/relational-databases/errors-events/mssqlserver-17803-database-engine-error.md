---
description: MSSQLSERVER_17803
title: MSSQLSERVER_17803 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17803 (Database Engine error)
ms.assetid: 28591a19-258d-4891-b78a-4686789bb2d7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 848adb2125fdc6ab7427fe076d430b2609d90196
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456403"
---
# <a name="mssqlserver_17803"></a>MSSQLSERVER_17803
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|17803|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SRV_NOMEMORY|  
|Meldungstext|Bei der Verbindungsherstellung ist ein Fehler bei der Speicherbelegung aufgetreten. Reduzieren Sie die vermeidbare Arbeitsspeicherlast, oder vergrößern Sie den Systemarbeitsspeicher. Die Verbindung wurde geschlossen.%.*ls|  
  
## <a name="explanation"></a>Erklärung  
Der Server verfügt nicht über genügend Arbeitsspeicher.  
  
## <a name="user-action"></a>Benutzeraktion  
Bestimmen Sie, warum der Server nicht über genügend Arbeitsspeicher verfügt. Allgemeine Schritte zur Behandlung von Problemen mit dem Arbeitsspeicher sind möglicherweise nützlich.  
  
