---
title: Festlegen der AUTO_SHRINK-Datenbankoption auf OFF | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 16403850-d745-4754-b84f-5f01aaecd24e
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: c48e0671052d612a52703aa7d367e03257cf1e14
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51667339"
---
# <a name="set-the-autoshrink-database-option-to-off"></a>Festlegen der AUTO_SHRINK-Datenbankoption auf OFF
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Diese Regel überprüft, ob die AUTO_SHRINK-Datenbankoption auf OFF festgelegt ist. Häufiges Verkleinern und Erweitern einer Datenbank kann zu physischer Fragmentierung führen.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Legen Sie die AUTO_SHRINK-Datenbankoption auf OFF fest. Wenn Sie wissen, dass der freigegebene Speicherplatz in Zukunft nicht benötigt wird, können Sie den Speicherplatz durch manuelles Verkleinern der Datenbank freigeben.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 Microsoft Knowledge Base-Artikel [315512](https://go.microsoft.com/fwlink/?linkid=117750)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
