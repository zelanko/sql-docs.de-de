---
title: Festlegen der AUTO_SHRINK-Datenbankoption auf OFF | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 16403850-d745-4754-b84f-5f01aaecd24e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c81885e5a3aaec197b8963c2e868b6f65a0b0544
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62691514"
---
# <a name="set-the-auto_shrink-database-option-to-off"></a>Festlegen der AUTO_SHRINK-Datenbankoption auf OFF
  Diese Regel überprüft, ob die AUTO_SHRINK-Datenbankoption auf OFF festgelegt ist. Häufiges Verkleinern und Erweitern einer Datenbank kann zu physischer Fragmentierung führen.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Legen Sie die AUTO_SHRINK-Datenbankoption auf OFF fest. Wenn Sie wissen, dass der freigegebene Speicherplatz in Zukunft nicht benötigt wird, können Sie den Speicherplatz durch manuelles Verkleinern der Datenbank freigeben.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 Microsoft Knowledge Base-Artikel [315512](https://go.microsoft.com/fwlink/?linkid=117750)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
