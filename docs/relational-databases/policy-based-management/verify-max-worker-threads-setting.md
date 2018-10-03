---
title: Überprüfen Sie die Max Worker Threads Einstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 2d94adfd-3ba1-493a-b29a-b436f9d583df
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 735d396830f3572faaa2683ccea72d68fbf802c8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752058"
---
# <a name="verify-max-worker-threads-setting"></a>Überprüfen der Einstellung 'Max. Anzahl von Arbeitsthreads'
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Diese Regel überprüft die Serveroption Max. Anzahl von Arbeitsthreads auf potenziell falsche Einstellungen. Das Festlegen der Option Max. Anzahl von Arbeitsthreads auf einen niedrigen Wert verhindert die prompte Reaktion vieler Threads auf eingehende Clientanforderungen, was dazu führen kann, dass Threads nicht mehr auf die CPU zugreifen können. Legen Sie die Option jedoch auf einen hohen Wert fest, wird möglicherweise Adressraum verschwendet, da jeder aktive Thread auf 64-Bit-Servern bis zu 4 MB Speicherplatz in Anspruch nimmt.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Legen Sie die max. Anzahl von NIB-Arbeitsthreads (Option) auf 0 fest. Dadurch ermittelt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] basierend auf den Benutzeranforderungen automatisch die richtige Anzahl aktiver Arbeitsthreads.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Konfigurieren der Serverkonfigurationsoption Maximale Anzahl von Arbeitsthreads](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
