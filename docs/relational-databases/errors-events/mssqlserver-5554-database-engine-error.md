---
description: MSSQLSERVER_5554
title: MSSQLSERVER_5554 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f8039ad4a6cfefcdbd4e72c583f520e36f273875
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470903"
---
# <a name="mssqlserver_5554"></a>MSSQLSERVER_5554
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|MSSQLSERVER|  
|Ereignis-ID|5554|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|FS_MINIVER_OVERFLOW|  
|Meldungstext|Das maximale Limit des Dateisystems an Versionen insgesamt für eine einzige Datei wurde erreicht.|  
  
## <a name="explanation"></a>Erklärung  
In MARS (Multiple Active Result Sets) oder Triggerszenarios verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Miniversion des Betriebssystems.  
  
## <a name="user-action"></a>Benutzeraktion  
Versuchen Sie, wiederholte Datenupdates in derselben Transaktion zu vermeiden.  
  
