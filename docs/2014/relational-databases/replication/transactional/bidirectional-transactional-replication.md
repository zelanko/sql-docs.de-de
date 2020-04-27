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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63188596"
---
# <a name="bidirectional-transactional-replication"></a>Bidirektionale Transaktionsreplikation
  Die bidirektionale Transaktionsreplikation stellt eine spezielle Transaktionsreplikationstopologie dar, über die zwei Server Änderungen austauschen können: Jeder Server veröffentlicht Daten und abonniert dann eine Veröffentlichung mit denselben Daten vom anderen Server. Der **@loopback_detection** -Parameter von [sp_addsubscription &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) auf true festgelegt ist, um sicherzustellen, dass Änderungen nur an den Abonnenten gesendet werden und nicht dazu führen, dass die Änderung zurück an den Verleger gesendet wird.  
  
 In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und höheren Versionen wird diese Topologie auch von der Peer-zu-Peer-Transaktionsreplikation unterstützt, doch kann die bidirektionale Replikation zu einer höheren Leistung führen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md)  
  
  
