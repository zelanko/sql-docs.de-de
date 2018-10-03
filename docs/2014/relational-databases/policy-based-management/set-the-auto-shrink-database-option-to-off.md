---
title: Festlegen der AUTO_SHRINK-Datenbankoption auf OFF | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 16403850-d745-4754-b84f-5f01aaecd24e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4cec33e2f4e394f11f20068c27e57df268fae81f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220410"
---
# <a name="set-the-autoshrink-database-option-to-off"></a>Festlegen der AUTO_SHRINK-Datenbankoption auf OFF
  Diese Regel überprüft, ob die AUTO_SHRINK-Datenbankoption auf OFF festgelegt ist. Häufiges Verkleinern und Erweitern einer Datenbank kann zu physischer Fragmentierung führen.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Legen Sie die AUTO_SHRINK-Datenbankoption auf OFF fest. Wenn Sie wissen, dass der freigegebene Speicherplatz in Zukunft nicht benötigt wird, können Sie den Speicherplatz durch manuelles Verkleinern der Datenbank freigeben.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 Microsoft Knowledge Base-Artikel [315512](http://go.microsoft.com/fwlink/?linkid=117750)  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
