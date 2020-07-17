---
title: MSSQLSERVER_17132 | Microsoft-Dokumentation
description: Der SQL Server-Computer konnte das Clientanmeldepaket nicht verarbeiten. Hier finden Sie eine Erläuterung des Fehlers sowie mögliche Lösungen.
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17132 (Database Engine error)
ms.assetid: d1d198bd-6730-4394-bd5f-28f320c01a38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4767ba217eab0d8cdbc6a9dc80f751868322f21f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780847"
---
# <a name="mssqlserver_17132"></a>MSSQLSERVER_17132
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|17132|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|INIT_NODESSPACE|  
|Meldungstext|Fehler beim Serverstart aufgrund von unzureichendem Arbeitsspeicher für den Deskriptor. Reduzieren Sie die vermeidbare Arbeitsspeicherlast, oder vergrößern Sie den Systemarbeitsspeicher.|  
  
## <a name="explanation"></a>Erklärung  
Fehler beim Zuordnen von ausreichend Arbeitsspeicher, um internen Serverdeskriptor zu speichern.  
  
## <a name="user-action"></a>Benutzeraktion  
Fügen Sie dem Computer mehr Arbeitsspeicher hinzu. Allgemeine Schritte zur Behandlung von Problemen mit dem Arbeitsspeicher sind möglicherweise nützlich.  
  
