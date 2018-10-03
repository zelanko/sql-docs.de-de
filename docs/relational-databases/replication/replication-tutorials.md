---
title: Tutorials zur Replikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/09/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- tutorials [SQL Server replication]
- walkthroughs [SQL Server replication]
- replication [SQL Server], tutorials
ms.assetid: 19fbd10e-5b59-4cd0-a988-52d5d9206242
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3e6b91d754c477efe14ee0d47192beff5c735138
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47784418"
---
# <a name="replication-tutorials"></a>Tutorials zur Replikation
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Die Replikation ist ein wichtiges Mittel zum Bewegen von Daten oder Teilmengen von Daten zwischen verschiedenen Servern. Sie können Daten auf mehreren Servern replizieren, die durch eine Transaktionsreplikation vollständig miteinander verbunden sind. Außerdem können Sie Daten auf Servern und Clients replizieren, die zeitweilig über eine Mergereplikation miteinander verbunden werden. In diesem Artikel sind Tutorials aufgeführt, die Ihnen dabei helfen sollen, Ihren Server auf Replikationen vorzubereiten. Außerdem erhalten Sie Informationen zum Konfigurieren der Transaktions- bzw. Mergereplikation. 
  
In den Tutorials zur Replikation bezieht sich „Verleger“ auf den Server, der die zu replizierenden Quelldaten enthält. „Abonnent“ bezieht sich auf den Zielserver. Verleger und Abonnent können dieselbe Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gemeinsam verwenden. Dies ist jedoch nicht obligatorisch. Weitere Informationen finden Sie in der [Übersicht über das Replikationsveröffentlichungsmodell](../../relational-databases/replication/publish/replication-publishing-model-overview.md).  

In diesen Tutorials wird NODE1\SQL2016 als Verleger und Verteiler verwendet. NODE2\SQL2016 wird als Abonnent verwendet. 
  
> [!NOTE]  
> Die meisten der in diesen Lernprogrammen vorgestellten Aufgaben können programmgesteuert ausgeführt werden. Weitere Informationen finden Sie in der [Replikation des Entwicklerhandbuchs](../../relational-databases/replication/concepts/replication-developer-documentation.md).  
  
## <a name="replication-tutorials"></a>Tutorials zur Replikation  
[Tutorial: Vorbereiten von SQL Server auf die Replikation (Verleger, Verteiler und Abonnent)](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md) 
 
Hier erfahren Sie, wie Server so vorbereitet werden, dass die Replikation mit geringsten Benutzerrechten ausgeführt werden kann. Es ist erforderlich, dieses Lernprogramm vor den anderen Lernprogrammen zur Replikation abzuschließen.  
  
[Tutorial: Konfigurieren der Replikation zwischen zwei Servern mit kontinuierlicher Verbindung (transaktional)](../../relational-databases/replication/tutorial-replicating-data-between-continuously-connected-servers.md)

Informationen zum Konfigurieren der Transaktionsreplikation zum Replizieren von Daten zwischen vollständig verbundenen Servern. Außerdem umfasst dieses Tutorial einige grundlegende Methoden zum Beheben von Fehlern. 

  
[Tutorial: Konfigurieren der Replikation zwischen einem Server und mobilen Clients (Mergereplikation)](../../relational-databases/replication/tutorial-replicating-data-with-mobile-clients.md)

Erfahren Sie, wie Daten mithilfe der Mergereplikation zwischen einem Server und mindestens einem Client ausgetauscht werden, die nur gelegentlich miteinander verbunden sind.  
  
## <a name="see-also"></a>Siehe auch  
[Sicherheit und Schutz (Replikation)](../../relational-databases/replication/security/security-and-protection-replication.md) 

[Transaktionsreplikation (Übersicht)](https://docs.microsoft.com/sql/relational-databases/replication/transactional/transactional-replication) 

[Mergereplikation (Übersicht)](https://docs.microsoft.com/sql/relational-databases/replication/merge/merge-replication)

  
