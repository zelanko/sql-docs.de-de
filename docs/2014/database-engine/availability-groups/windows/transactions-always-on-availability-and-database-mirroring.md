---
title: Datenbankübergreifende Transaktionen nicht unterstützt für Datenbankspiegelungs- oder AlwaysOn-Verfügbarkeitsgruppen (SQLServer) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- cross-database transactions [SQL Server]
- transactions [database mirroring]
- Availability Groups [SQL Server], interoperability
- troubleshooting [SQL Server], cross-database transactions
ms.assetid: 9f7ed895-ad65-43e3-ba08-00d7bff1456d
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: fdfb419c6200cc185128332d790f554c9b10efd3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048556"
---
# <a name="cross-database-transactions-not-supported-for-database-mirroring-or-alwayson-availability-groups-sql-server"></a>Datenbankübergreifende Transaktionen nicht unterstützt für Datenbankspiegelungs- oder AlwaysOn-Verfügbarkeitsgruppen (SQL Server)
  Datenbankübergreifende Transaktionen und verteilte Transaktionen werden von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] oder der Datenbankspiegelung nicht unterstützt. Dies ist darauf zurückzuführen, dass die Unteilbarkeit/Vollständigkeit von Transaktionen aus folgenden Gründen nicht gewährleistet werden kann:  
  
-   Für datenbankübergreifende Transaktionen: Jede Datenbank führt einen unabhängigen Commit aus. Aus diesem Grund kann sogar für Datenbanken in einer einzelnen Verfügbarkeitsgruppe ein Failover auftreten, nachdem eine Datenbank für eine Transaktion einen Commit ausgeführt hat, jedoch bevor die andere Datenbank diesen Schritt ausgeführt hat. Bei der Datenbankspiegelung wird dieses Problem verstärkt, da die gespiegelte Datenbank sich nach einem Failover in der Regel auf einer anderen Serverinstanz der anderen Datenbank befindet. Auch wenn beide Datenbanken zwischen denselben beiden Partnern gespiegelt werden, ist nicht garantiert, dass das Failover für beide Datenbanken gleichzeitig ausgeführt wird.  
  
-   Für verteilte Transaktionen: Nach einem Failover kann vom neuen Prinzipalserver bzw. vom primären Replikat keine Verbindung mit dem verteilten Transaktionskoordinator auf dem vorherigen Prinzipalserver bzw. primären Replikat hergestellt werden. Aus diesem Grund kann der neue Prinzipalserver bzw. das neue primäre Replikat den Transaktionsstatus nicht erlangen.  
  
 Im folgenden Beispiel zur Datenbankspiegelung wird verdeutlicht, wie eine logische Inkonsistenz auftreten kann. In diesem Beispiel fügt eine Anwendung über eine datenbankübergreifende Transaktion zwei Datenzeilen ein: Eine Zeile wird in eine Tabelle in einer gespiegelten Datenbank (A) eingefügt, und die andere Zeile wird in eine Tabelle in einer anderen Datenbank (B) eingefügt. Datenbank A wird im Modus für hohe Sicherheit mit automatischem Failover gespiegelt. Während des Commits der Transaktion fällt Datenbank A aus. Die Spiegelungssitzung führt automatisch ein Failover zum Spiegel von Datenbank A aus.  
  
 Nach dem Failover kann ein Commit der datenbankübergreifenden Transaktion möglicherweise erfolgreich für Datenbank B ausgeführt werden, jedoch nicht für die Datenbank, für die der Failover ausgeführt wurde. Dies wäre möglich, wenn der ursprüngliche Prinzipalserver für Datenbank A nicht das Protokoll für die datenbankübergreifende Transaktion vor dem Ausfall an den Spiegelserver gesendet hätte. Nach dem Failover wäre diese Transaktion auf dem neuen Prinzipalserver nicht vorhanden. Datenbanken A und B würden inkonsistent werden, da die in Datenbank B eingefügten Daten erhalten bleiben, während die in Datenbank A eingefügten Daten verloren gingen.  
  
 Ein vergleichbares Szenario kann bei einer MS DTC-Transaktion auftreten. Angenommen, der neue Prinzipal setzt sich nach dem Failover mit MS DTC in Verbindung. Der neue Prinzipalserver ist MS DTC jedoch nicht bekannt, deshalb beendet er alle Transaktionen, für die "ein Commit vorbereitet wird", für die in anderen Datenbanken jedoch bereits anscheinend ein Commit ausgeführt wurde.  
  
> [!IMPORTANT]  
>  Eine SQL Server-Installation wird auch unterstützt, wenn Datenbankspiegelungsfunktionen oder Verfügbarkeitsgruppen zusammen mit DTC verwendet werden. Wenn eine Datenbank jedoch Teil einer Datenbank-Spiegelungssitzung ist oder eine Verfügbarkeitsgruppe und DTC ebenfalls in der Datenbank verwendet werden, geht Microsoft Supportproblemen nur dann nach, wenn sie nicht in Zusammenhang mit der kombinierten Verwendung der Datenbankspiegelungsfunktionen oder Verfügbarkeitsgruppen mit DTC stehen.  
  
  