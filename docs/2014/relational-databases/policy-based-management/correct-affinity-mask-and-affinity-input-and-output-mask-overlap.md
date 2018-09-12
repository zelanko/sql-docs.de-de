---
title: Richtige Affinity Mask und Affinity Input-Output Mask überlappen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1a0da6df-57ff-4f3f-aae9-2fbc4897508c
caps.latest.revision: 11
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 55cb5db43f91a50e614ae651772f684d50127cf5
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43815252"
---
# <a name="correct-affinity-mask-and-affinity-input-output-mask-overlap"></a>Richtige Affinity Mask und Affinity Input-Output Überlappung
  Diese Regel überprüft, ob die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] über einen oder mehrere Prozessoren verfügt, die sowohl für die Verwendung mit der Option Affinity Mask als auch mit der Option Affinity I/O Mask zugeordnet wurde. Auf einem Computer, der über einen oder mehrere Prozessoren verfügt, bestimmen die Optionen Affinity Mask und Affinity I/O Mask, welche CPUs von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet werden. Das Aktivieren einer CPU mit den beiden Optionen Affinity Mask und Affinity I/O Mask kann die Leistung beeinträchtigen, da die Prozessoren übermäßig beansprucht werden.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Wenn Sie entweder die Option Affinity Mask oder die Option Affinity I/O Mask festlegen, sollten Sie beide Optionen festlegen, jedoch jede CPU nicht mehr als einmal aktivieren.  
  
 Aktivieren Sie in den Optionen Affinity Mask und Affinity I/O Mask nicht dieselbe CPU. Die Bits, die den einzelnen CPUs entsprechen, sollten sich jeweils in einem der folgenden Zustände befinden:  
  
-   0 für die Option Affinity Mask und die Option Affinity I/O Mask  
  
-   0 für die Option Affinity Mask und 1 für die Option Affinity I/O Mask  
  
-   1 für die Option Affinity Mask und 0 für die Option Affinity I/O Mask  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Affinitätsmaske (Serverkonfigurationsoption)](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)  
  
 [Affinity I/O Mask (Serverkonfigurationsoption)](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md)  
  
 [Affinity64 Mask (Serverkonfigurationsoption)](../../database-engine/configure-windows/affinity64-mask-server-configuration-option.md)  
  
 [affinity64 I/O mask (Serverkonfigurationsoption)](../../database-engine/configure-windows/affinity64-input-output-mask-server-configuration-option.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
