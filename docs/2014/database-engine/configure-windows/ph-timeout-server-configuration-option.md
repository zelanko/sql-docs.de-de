---
title: PH-Timeout (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 25a89c00466cf4a702202f6a6fb4959f1d845c41
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62781338"
---
# <a name="ph-timeout-server-configuration-option"></a>PH-Timeout (Serverkonfigurationsoption)
  Verwenden Sie die Option „ph timeout“, um in Sekunden anzugeben, wie lange der Volltext-Protokollhandler auf eine Verbindung mit der Datenbank warten soll, bevor ein Timeout eintritt. Der Standardwert beträgt 60 Sekunden. Vergrößern Sie den Wert für ph timeout, wenn bei Verbindungsversuchen aufgrund von vorübergehenden Netzwerkproblemen Timeouts auftreten.  
  
 Der Volltext-Protokollhandler wird von dem Filterdämonhost gehostet und wird dazu verwendet, aus SQL Server die Daten zum Erstellen des Volltextindexes abzurufen. Weitere Informationen zu den Komponenten der Volltextsuche finden Sie unter [Volltextsuche](../../relational-databases/search/full-text-search.md).  
  
 Wenn der Protokollhandler zum Abrufen einer Datenzeile innerhalb der angegebenen Zeit keine Verbindung mit SQL Server herstellen kann, wird ein Timeoutfehler für diese Zeile gemeldet. Der Volltext-Gatherer versucht, diese Zeile zu einem späteren Zeitpunkt erneut abzurufen. Weitere Informationen zum Volltext-Gatherer finden Sie unter [Auffüllen von Volltextindizes](../../relational-databases/indexes/indexes.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Volltextsuche](../../relational-databases/search/full-text-search.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
