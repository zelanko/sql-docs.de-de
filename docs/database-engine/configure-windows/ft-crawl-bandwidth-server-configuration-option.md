---
title: Bandbreite für Volltextdurchforstung (Serverkonfigurationsoption) | Microsoft-Dokumentation
description: Informationen zur Option „ft crawl bandwidth“ Hier erfahren Sie, wie diese Option sich auf die Anzahl der Puffer auswirkt, die SQL Server im Pool der großen Arbeitsspeicherpuffer speichert.
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
- large memory buffers
- memory [SQL Server], buffers
- ft crawl bandwidth option
ms.assetid: e5864ad9-92f5-43b5-95de-46d68ded8694
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 59caa1e868c4caab24afd17909c34f57c96f0005
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85789786"
---
# <a name="ft-crawl-bandwidth-server-configuration-option"></a>Bandbreite für Volltextdurchforstung (Serverkonfigurationsoption)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Verwenden Sie die Option **ft crawl bandwidth** , um anzugeben, auf welche Größe der Pool von großen Speicherpuffern erhöht werden kann. Große Speicherpuffer sind 4 Megabyte (MB) groß. Der **max** -Parameterwert gibt die maximale Anzahl der Puffer an, die der Volltextspeicher-Manager in einem großen Pufferpool verwalten soll. Wenn der **max** -Wert gleich null ist, gibt es keine obere Grenze für die Anzahl der Puffer in einem großen Pufferpool.  
  
 Der **min** -Parameter gibt die minimale Anzahl der Speicherpuffer an, die im großen Speicherpufferpool verwaltet werden müssen. Auf Anforderung vom [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Speicher-Manager werden alle zusätzlichen Pufferpools freigegeben, die Mindestzahl an Puffern wird jedoch beibehalten. Ist der angegebene **min** -Wert jedoch gleich null, werden alle Speicherpuffer freigegeben.  
  
 Unter diesen Umständen ist die Anzahl der Puffer, die derzeit zugewiesen sind, kleiner als der vom **min** -Parameter angegebene Wert.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Bandbreite für Volltextbenachrichtigung (Serverkonfigurationsoption)](../../database-engine/configure-windows/ft-notify-bandwidth-server-configuration-option.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
