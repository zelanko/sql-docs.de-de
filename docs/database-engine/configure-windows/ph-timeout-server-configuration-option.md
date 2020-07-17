---
title: PH-Timeout (Serverkonfigurationsoption) | Microsoft-Dokumentation
description: Informationen zur Option „PH_timeout“ Hier erfahren Sie, wie diese die Zeit einschränkt, die dem Volltext-Protokollhandler für die Verbindungsherstellung mit einer SQL Server-Datenbank zugeteilt wird.
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a0173d6e5c5b10ac05b757f483518999fc526992
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730964"
---
# <a name="ph-timeout-server-configuration-option"></a>PH-Timeout (Serverkonfigurationsoption)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Verwenden Sie die Option „ph timeout“, um in Sekunden anzugeben, wie lange der Volltext-Protokollhandler auf eine Verbindung mit der Datenbank warten soll, bevor ein Timeout eintritt. Der Standardwert beträgt 60 Sekunden. Vergrößern Sie den Wert für ph timeout, wenn bei Verbindungsversuchen aufgrund von vorübergehenden Netzwerkproblemen Timeouts auftreten.  
  
 Der Volltext-Protokollhandler wird von dem Filterdämonhost gehostet und wird dazu verwendet, aus SQL Server die Daten zum Erstellen des Volltextindexes abzurufen. Weitere Informationen zu den Komponenten der Volltextsuche finden Sie unter [Volltextsuche](../../relational-databases/search/full-text-search.md).  
  
 Wenn der Protokollhandler zum Abrufen einer Datenzeile innerhalb der angegebenen Zeit keine Verbindung mit SQL Server herstellen kann, wird ein Timeoutfehler für diese Zeile gemeldet. Der Volltext-Gatherer versucht, diese Zeile zu einem späteren Zeitpunkt erneut abzurufen. Weitere Informationen zum Volltext-Gatherer finden Sie unter [Auffüllen von Volltextindizes](../../relational-databases/search/populate-full-text-indexes.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Volltextsuche](../../relational-databases/search/full-text-search.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
