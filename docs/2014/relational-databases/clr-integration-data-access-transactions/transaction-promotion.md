---
title: Transaktionshöherstufung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- distributed transactions [CLR integration]
- promoting transactions [CLR integration]
- Enlist keyword
- transaction promotion [CLR integration]
ms.assetid: 5bc7e26e-28ad-4198-a40d-8b2c648ba304
caps.latest.revision: 13
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 789fa82f6afc23c09028726c837ff5d37a082a06
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37349242"
---
# <a name="transaction-promotion"></a>Transaktionshöherstufung
  Die *Transaktionshöherstufung* besteht darin, eine leichtgewichtige lokale Transaktion bei Bedarf automatisch zu einer vollständig verteilbaren Transaktion umzuwandeln. Wird in einer Datenbanktransaktion auf dem Server eine verwaltete gespeicherte Prozedur aufgerufen, wird der CLR-Code (Common Language Runtime, CLR) im Kontext einer lokalen Transaktion ausgeführt.  Wenn in der Datenbanktransaktion eine Verbindung zu einem Remoteserver geöffnet wird, wird die Verbindung in die verteilte Transaktion eingetragen, und die lokale Transaktion wird automatisch zu einer verteilten Transaktion höhergestuft. Dies bedeutet, dass durch die Transaktionhöherstufung der Verarbeitungsaufwand von verteilten Transaktionen reduziert wird, indem diese erst dann erstellt werden, wenn sie gebraucht werden. Transaktionshöherstufung ist automatisch, wenn es aktiviert wurde mithilfe der `Enlist` -Schlüsselwort, und erfordert keinen Eingriff seitens des Entwicklers. Der .NET Framework-Datenanbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bietet über die Klassen im .NET Framework-`System.Data.SqlClient`-Namespace Unterstützung für die Transaktionshöherstufung.  
  
## <a name="the-enlist-keyword"></a>Das 'Enlist'-Schlüsselwort  
 Die `ConnectionString`-Eigenschaft eines `SqlConnection`-Objekts unterstützt das `Enlist`-Schlüsselwort, welches angibt, ob `System.Data.SqlClient` den Transaktionskontext erkennt und die Verbindung automatisch in eine verteilte Transaktion einträgt. Wenn für dieses Schlüsselwort true festgelegt wird, wird die Verbindung automatisch im aktuellen Transaktionskontext des öffnenden Threads eingetragen. Wenn für dieses Schlüsselwort false festgelegt wird, interagiert die SqlClient-Verbindung nicht mit einer verteilten Transaktion. Wenn das `Enlist`-Schlüsselwort nicht in der Verbindungszeichenfolge angegeben wird, wird die Verbindung automatisch in eine verteilte Transaktion eingetragen, falls zum Zeitpunkt des Öffnens der Verbindung eine verteilte Transaktion erkannt wurde.  
  
## <a name="distributed-transactions"></a>Verteilte Transaktionen  
 Verteilte Transaktionen nehmen normalerweise beträchtliche Systemressourcen in Anspruch. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) verwaltet diese Transaktionen und integriert alle Ressourcen-Manager, auf die in den Transaktionen zugegriffen wird. Andererseits handelt es sich bei der Transaktionhöherstufung um eine besondere Form der `System.Transactions`-Transaktion, mit der die Verarbeitung an eine einfache [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Transaktion delegiert wird. `System.Transactions`, `System.Data.SqlClient`, und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] koordinieren die Arbeit zur Behandlung der Transaktions, Stufen sie bei Bedarf auf eine vollständig verteilte Transaktion hoch.  
  
 Der Vorteil der Verwendung der Transaktionshöherstufung liegt darin, dass beim Öffnen einer Verbindung, die eine aktive `TransactionScope`-Transaktion aufweist, diese Transaktion als "leichtgewichtige" Transaktion agiert, wenn keine anderen Verbindungen geöffnet sind, anstatt als verteilte Transaktion zusätzliche Ressourcen zu verbrauchen. Weitere Informationen zu `TransactionScope`, finden Sie unter [Using System.Transactions](../native-client-ole-db-transactions/transactions.md).  
  
## <a name="see-also"></a>Siehe auch  
 [CLR-Integration und -Transaktionen](clr-integration-and-transactions.md)  
  
  
