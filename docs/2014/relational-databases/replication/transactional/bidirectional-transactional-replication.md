---
title: Bidirektionale Transaktionsreplikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a2cf5fbf215338b273be0924e6930906c8698aff
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188596"
---
# <a name="bidirectional-transactional-replication"></a>Bidirektionale Transaktionsreplikation
  Die bidirektionale Transaktionsreplikation stellt eine spezielle Transaktionsreplikationstopologie dar, über die zwei Server Änderungen austauschen können: Jeder Server veröffentlicht Daten und abonniert dann eine Veröffentlichung mit denselben Daten vom anderen Server. Der **@loopback_detection**-Parameter von [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) ist auf TRUE festgelegt, um sicherzustellen, dass Änderungen nur an den Abonnenten gesendet werden und um zu verhindern, dass die Änderung wieder zurück auf den Verleger gelangt.  
  
 In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und höheren Versionen wird diese Topologie auch von der Peer-zu-Peer-Transaktionsreplikation unterstützt, doch kann die bidirektionale Replikation zu einer höheren Leistung führen.  
  
## <a name="see-also"></a>Siehe auch  
 [Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md)  
  
  
