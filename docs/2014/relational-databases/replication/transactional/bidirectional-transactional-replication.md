---
title: Bidirektionale Transaktionsreplikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 86cdfaa9e7bf61b76acb953e3f2c6a1feb7d1dad
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126797"
---
# <a name="bidirectional-transactional-replication"></a>Bidirektionale Transaktionsreplikation
  Die bidirektionale Transaktionsreplikation stellt eine spezielle Transaktionsreplikationstopologie dar, über die zwei Server Änderungen austauschen können: Jeder Server veröffentlicht Daten und abonniert dann eine Veröffentlichung mit denselben Daten vom anderen Server. Der **@loopback_detection**-Parameter von [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) ist auf TRUE festgelegt, um sicherzustellen, dass Änderungen nur an den Abonnenten gesendet werden und um zu verhindern, dass die Änderung wieder zurück auf den Verleger gelangt.  
  
 In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und höheren Versionen wird diese Topologie auch von der Peer-zu-Peer-Transaktionsreplikation unterstützt, doch kann die bidirektionale Replikation zu einer höheren Leistung führen.  
  
## <a name="see-also"></a>Siehe auch  
 [Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md)  
  
  
