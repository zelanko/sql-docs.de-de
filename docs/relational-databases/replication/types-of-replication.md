---
title: Replikationstypen | Microsoft-Dokumentation
description: Lernen Sie die verschiedenen Replikationstypen kennen, die SQL Server für die Verwendung in verteilten Anwendungen bereitstellt.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], types
ms.assetid: c1655e8d-d14c-455a-a7f9-9d2f43e88ab4
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: c581a9d715e231fc593100549b3704b531292ed2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85720681"
---
# <a name="types-of-replication"></a>Replikationstypen
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/applies-to-version/sql-asdb.md)]
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stehen für die Verwendung in verteilten Anwendungen die folgenden Replikationstypen zur Verfügung:  

| **Typ** | **Beschreibung** |
|:-------- | :-------------- |
| [Transaktionsreplikation](transactional/transactional-replication.md)| Änderungen auf dem Verleger werden an den Abonnenten übermittelt, sobald sie auftreten (nahezu in Echtzeit). Die Datenänderungen werden auf dem Abonnenten in derselben Reihenfolge und mit denselben Transaktionsgrenzen angewendet, in der sie auf dem Verleger stattgefunden haben. | 
| [Mergereplikation](merge/merge-replication.md) | Daten können sowohl auf dem Verleger als auch auf dem Abonnenten geändert werden und werden mit Triggern nachverfolgt. Ist eine Verbindung mit dem Netzwerk vorhanden, nimmt der Abonnent eine Synchronisierung mit dem Verleger vor und tauscht alle Zeilen aus, die sich seit der letzten Synchronisierung auf dem Verleger und dem Abonnenten geändert haben. | 
| [Momentaufnahmereplikation](snapshot-replication.md) | Wendet eine Momentaufnahme vom Verleger auf den Abonnenten an, der die Daten genau so verteilt, wie Sie zu einem bestimmten Zeitpunkt angezeigt werden, ohne Aktualisierungen an den Daten zu überwachen. Bei der Synchronisierung wird die gesamte Momentaufnahmen generiert und an Abonnenten gesendet.| 
| [Peer-zu-Peer](transactional/peer-to-peer-transactional-replication.md) | Auf der Grundlage der Transaktionsreplikation aufbauend, gibt die Peer-zu-Peer-Replikation transaktionskonsistente Änderungen fast in Echtzeit zwischen mehreren Serverinstanzen weiter. | 
| [Bidirektional](transactional/bidirectional-transactional-replication.md)| Die bidirektionale Transaktionsreplikation stellt eine spezielle Transaktionsreplikationstopologie dar, über die zwei Server Änderungen austauschen können: Jeder Server veröffentlicht Daten und abonniert dann eine Veröffentlichung mit denselben Daten vom anderen Server. | 
| [Aktualisierbare Abonnements](transactional/updatable-subscriptions-for-transactional-replication.md) | Diese basieren auf der Grundlage der Transaktionsreplikation. Wenn Daten auf einem Abonnenten für ein aktualisierbares Abonnement aktualisiert werden, werden Sie zuerst an den Verleger weitergegeben und dann an andere Abonnenten. | 
  
 
Für welchen Replikationstyp Sie sich bei Ihrer konkreten Anwendung entscheiden sollten, hängt von vielen Faktoren ab. So müssen z. B. die physische Replikationsumgebung, die Art und Menge der zu replizierenden Daten und die Frage berücksichtigt werden, ob die Daten auf dem Abonnenten aktualisiert werden. Bei der physischen Umgebung sind die Anzahl und der Standort der Computer in Betracht zu ziehen, die in die Replikation mit einbezogen werden sollen. Außerdem muss berücksichtigt werden, ob es sich bei diesen Computern um Clients (Arbeitsstationen, Laptops bzw. Handhelds) oder Server handelt.  
  
Unabhängig vom jeweiligen Typ beginnen alle Replikationen typischerweise mit einer Erstsynchronisierung der veröffentlichten Objekte auf dem Verleger und den Abonnenten. Diese Erstsynchronisierung kann durch eine Replikation mit einer *Momentaufnahme*ausgeführt werden. Die Momentaufnahme ist eine Kopie aller in einer Veröffentlichung enthaltenen Objekte und Daten. Diese Momentaufnahme wird an die Abonnenten weitergegeben. Bei einigen Anwendungen ist lediglich eine Momentaufnahmereplikation erforderlich. Bei anderen Anwendungstypen hingegen ist es wichtig, dass nachfolgende Datenänderungen inkrementell an den Abonnenten weitergeleitet werden. Es gibt auch Anwendungen, bei denen Änderungen vom Abonnenten zurück an den Verleger fließen müssen. Für solche Anwendungstypen bieten die Transaktionsreplikation und die Mergereplikation entsprechende Optionen.  
  
 
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über Replikations-Agents](../../relational-databases/replication/agents/replication-agents-overview.md)
  
  
