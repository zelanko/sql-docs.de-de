---
title: Updates zulassen (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
caps.latest.revision: 32
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: df8f7533f3e0ff76117d6a0e343d72a761708352
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="allow-updates-server-configuration-option"></a>Updates zulassen (Serverkonfigurationsoption)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Diese Option ist in der gespeicherten Prozedur **sp_configure** weiterhin vorhanden, obwohl ihre Funktionalität nicht in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zur Verfügung steht. (Die Einstellung hat keine Auswirkungen.) Für Systemtabellen werden keine direkten Updates unterstützt.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 Wird die Option **Updates zulassen** geändert, führt dies zu einem Fehler bei der RECONFIGURE-Anweisung. Änderungen an der Option **Updates zulassen** sollten aus allen Skripts entfernt werden.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
