---
title: Überprüfen Sie die Max Worker Threads Einstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 2d94adfd-3ba1-493a-b29a-b436f9d583df
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 861e24cf64a29d55a01fc9a10300e4174cd76d5f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62676961"
---
# <a name="verify-max-worker-threads-setting"></a>Überprüfen der Einstellung 'Max. Anzahl von Arbeitsthreads'
  Diese Regel überprüft die Serveroption Max. Anzahl von Arbeitsthreads auf potenziell falsche Einstellungen. Das Festlegen der Option Max. Anzahl von Arbeitsthreads auf einen niedrigen Wert verhindert die prompte Reaktion vieler Threads auf eingehende Clientanforderungen, was dazu führen kann, dass Threads nicht mehr auf die CPU zugreifen können. Legen Sie die Option jedoch auf einen hohen Wert fest, wird möglicherweise Adressraum verschwendet, da jeder aktive Thread auf 32-Bit-Servern 512 KB und auf 64-Bit-Servern 4 MB Speicherplatz in Anspruch nimmt.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Legen Sie die max. Anzahl von NIB-Arbeitsthreads (Option) auf 0 fest. Dadurch ermittelt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] basierend auf den Benutzeranforderungen automatisch die richtige Anzahl aktiver Arbeitsthreads.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Konfigurieren der Serverkonfigurationsoption Maximale Anzahl von Arbeitsthreads](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
