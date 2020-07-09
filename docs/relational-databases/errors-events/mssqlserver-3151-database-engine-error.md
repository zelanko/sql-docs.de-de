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
ms.openlocfilehash: d0d4c51bd7f4e1eca3bf57fbcfa89aec93357fb0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723739"
---
# <a name="mssqlserver_3151"></a>MSSQLSERVER_3151
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|3151|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LDDB_MASTER_LOAD_FAILED|  
|Meldungstext|Fehler beim Wiederherstellen der master-Datenbank. SQL Server wird heruntergefahren. Überprüfen Sie die Fehlerprotokolle, und erstellen Sie die master-Datenbank neu. Weitere Informationen zum Neuerstellen der master-Datenbank finden Sie in der SQL Server-Onlinedokumentation.|  
  
## <a name="explanation"></a>Erklärung  
Dies ist eine allgemeine Fehlermeldung, die auf verschiedene Probleme bei der **master**-Datenbank verweist.  
  
## <a name="user-action"></a>Benutzeraktion  
Überprüfen Sie das Fehlerprotokoll auf weitere Informationen. Führen Sie zum Erstellen einer verwendbaren **master**-Datenbank Setup.exe mit der Option REBUILDDATABASE aus. Weitere Informationen finden Sie weiter unten in diesem Thema im Abschnitt „Vorgehensweise: Installieren von SQL Server von der Eingabeaufforderung“ in der SQL Server-Onlinedokumentation.  
  
