---
title: MSSQLSERVER_3151 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 18db8cfd54a9df36564d64c0cd94407bfefb21f5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914794"
---
# <a name="mssqlserver3151"></a>MSSQLSERVER_3151
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|3151|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LDDB_MASTER_LOAD_FAILED|  
|Meldungstext|Fehler beim Wiederherstellen der master-Datenbank. SQL Server wird heruntergefahren. Überprüfen Sie die Fehlerprotokolle, und erstellen Sie die master-Datenbank neu. Weitere Informationen zum Neuerstellen der master-Datenbank finden Sie in der SQL Server-Onlinedokumentation.|  
  
## <a name="explanation"></a>Erklärung  
Dies ist eine allgemeine Fehlermeldung, die auf verschiedene Probleme bei der **master**-Datenbank verweist.  
  
## <a name="user-action"></a>Benutzeraktion  
Überprüfen Sie das Fehlerprotokoll auf weitere Informationen. Führen Sie zum Erstellen einer verwendbaren **master**-Datenbank Setup.exe mit der Option REBUILDDATABASE aus. Weitere Informationen finden Sie unter "Vorgehensweise: Installieren von SQLServer über die Eingabeaufforderung"in SQL Server-Onlinedokumentation.  
  
