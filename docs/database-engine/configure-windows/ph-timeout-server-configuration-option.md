---
title: PH-Timeout (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- time limit for protocol handler wait [SQL Server]
- timeout options [SQL Server], ph timeout option
- protocols [SQL Server], timing out
- ph timeout option
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fca08d3b59c9d7c53713ad3ec74c439dddc57c07
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798818"
---
# <a name="ph-timeout-server-configuration-option"></a>PH-Timeout (Serverkonfigurationsoption)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Verwenden Sie die Option „ph timeout“, um in Sekunden anzugeben, wie lange der Volltext-Protokollhandler auf eine Verbindung mit der Datenbank warten soll, bevor ein Timeout eintritt. Der Standardwert ist 60 Sekunden. Vergrößern Sie den Wert für ph timeout, wenn bei Verbindungsversuchen aufgrund von vorübergehenden Netzwerkproblemen Timeouts auftreten.  
  
 Der Volltext-Protokollhandler wird von dem Filterdämonhost gehostet und wird dazu verwendet, aus SQL Server die Daten zum Erstellen des Volltextindexes abzurufen. Weitere Informationen zu den Komponenten der Volltextsuche finden Sie unter [Volltextsuche](../../relational-databases/search/full-text-search.md).  
  
 Wenn der Protokollhandler zum Abrufen einer Datenzeile innerhalb der angegebenen Zeit keine Verbindung mit SQL Server herstellen kann, wird ein Timeoutfehler für diese Zeile gemeldet. Der Volltext-Gatherer versucht, diese Zeile zu einem späteren Zeitpunkt erneut abzurufen. Weitere Informationen zum Volltext-Gatherer finden Sie unter [Auffüllen von Volltextindizes](../../relational-databases/search/populate-full-text-indexes.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Volltextsuche](../../relational-databases/search/full-text-search.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
