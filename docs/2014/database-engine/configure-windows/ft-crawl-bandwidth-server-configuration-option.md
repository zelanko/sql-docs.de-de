---
title: Bandbreite für Volltextdurchforstung (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- large memory buffers
- memory [SQL Server], buffers
- ft crawl bandwidth option
ms.assetid: e5864ad9-92f5-43b5-95de-46d68ded8694
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f603987608a4c6456e01efc171bc93301069f046
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "52639348"
---
# <a name="ft-crawl-bandwidth-server-configuration-option"></a>Bandbreite für Volltextdurchforstung (Serverkonfigurationsoption)
  Verwenden Sie die Option **ft crawl bandwidth** , um anzugeben, auf welche Größe der Pool von großen Speicherpuffern erhöht werden kann. Große Speicherpuffer sind 4 Megabyte (MB) groß. Der **max** -Parameterwert gibt die maximale Anzahl der Puffer an, die der Volltextspeicher-Manager in einem großen Pufferpool verwalten soll. Wenn der **max** -Wert gleich null ist, gibt es keine obere Grenze für die Anzahl der Puffer in einem großen Pufferpool.  
  
 Der **min** -Parameter gibt die minimale Anzahl der Speicherpuffer an, die im großen Speicherpufferpool verwaltet werden müssen. Auf Anforderung vom [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Speicher-Manager werden alle zusätzlichen Pufferpools freigegeben, die Mindestzahl an Puffern wird jedoch beibehalten. Ist der angegebene **min** -Wert jedoch gleich null, werden alle Speicherpuffer freigegeben.  
  
 Unter diesen Umständen ist die Anzahl der Puffer, die derzeit zugewiesen sind, kleiner als der vom **min** -Parameter angegebene Wert.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [Bandbreite für Volltextbenachrichtigung (Serverkonfigurationsoption)](ft-notify-bandwidth-server-configuration-option.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
