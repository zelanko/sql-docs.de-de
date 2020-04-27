---
title: MSSQLSERVER_3151 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 18db8cfd54a9df36564d64c0cd94407bfefb21f5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62914794"
---
# <a name="mssqlserver_3151"></a>MSSQLSERVER_3151
    
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
 Überprüfen Sie das Fehlerprotokoll auf weitere Informationen. Führen Sie zum Erstellen einer verwendbaren **master**-Datenbank Setup.exe mit der Option REBUILDDATABASE aus. Weitere Informationen finden Sie unter "Vorgehensweise: Installieren von SQL Server von der Eingabeaufforderung" in der SQL Server-Onlinedokumentation.  
  
  
