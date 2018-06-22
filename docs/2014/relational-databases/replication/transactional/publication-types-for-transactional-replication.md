---
title: Veröffentlichungstypen der Transaktionsreplikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transactional replication, publications
ms.assetid: ad66aa34-3e37-401e-a6a1-fc1514eb6d50
caps.latest.revision: 31
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 11e9e6ffafe62c66684470b4b04e2e0b67cc868b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048695"
---
# <a name="publication-types-for-transactional-replication"></a>Veröffentlichungstypen der Transaktionsreplikation
  Die Transaktionsreplikation stellt drei Veröffentlichungstypen bereit:  
  
|Veröffentlichungstyp|Description|  
|----------------------|-----------------|  
|Standardmäßige Transaktionsveröffentlichung|Geeignet für Topologien, in denen alle Daten auf dem Abonnenten schreibgeschützt sind (von der Transaktionsreplikation wird dies auf dem Abonnenten nicht erzwungen).<br /><br /> Diese Transaktionsveröffentlichungen werden standardmäßig bei der Verwendung von Transact-SQL oder Replikationsverwaltungsobjekten (RMO) erstellt. Im Assistenten für neue Veröffentlichung werden sie erstellt, wenn auf der Seite **Veröffentlichungstyp** die Option **Transaktionsveröffentlichung** ausgewählt wird.<br /><br /> Weitere Informationen zum Erstellen von Veröffentlichungen finden Sie unter [Veröffentlichen von Daten und Datenbankobjekten](../publish/publish-data-and-database-objects.md).|  
|Transaktionsveröffentlichung in einer Peer-zu-Peer-Topologie|Dieser Veröffentlichungstyp weist die folgenden Merkmale auf:<br /><br /> Jeder Server verfügt über identische Daten und fungiert gleichzeitig als Verleger und Abonnent.<br /><br /> Dieselbe Zeile kann nur jeweils an einer Stelle geändert werden.<br /><br /> Diese Topologie eignet sich für Serverumgebungen am besten, die Hochverfügbarkeit und Leseskalierbarkeit erfordern.<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md).|  
  
## <a name="see-also"></a>Siehe auch  
 [Transaktionsreplikation](transactional-replication.md)  
  
  