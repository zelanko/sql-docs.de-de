---
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
ms.openlocfilehash: 61844f1818693f639941a334efcefb457c5ea092
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "67985090"
---
# <a name="mssqlserver_5554"></a>MSSQLSERVER_5554
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
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
  
