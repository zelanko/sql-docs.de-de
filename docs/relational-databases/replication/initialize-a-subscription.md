---
title: Initialisieren eines Abonnements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], initializing subscriptions
- transactional replication, initializing subscriptions
- initializing subscriptions [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], about initializing subscriptions
- merge replication [SQL Server replication], initializing subscriptions
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a7cd8c4ce33d34faba4507cfeb9dbe83a81f3bc7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47607519"
---
# <a name="initialize-a-subscription"></a>Initialisieren eines Abonnements
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Abonnenten in einer Replikationstopologie müssen initialisiert werden, damit sie für jeden Artikel in der Veröffentlichung, die sie abonniert haben, eine Kopie des Schemas sowie alle erforderlichen Replikationsobjekte (gespeicherte Prozeduren, Trigger, Metadatentabellen usw.) erhalten. Darüber hinaus erhält der Abonnent typischerweise einen Anfangsdatensatz. Die Standardinitialisierungsmethode verwendet eine vollständige Momentaufnahme mit Schema, Replikationsobjekten und Daten. Veröffentlichungen können aber auch ohne eine vollständige Momentaufnahme initialisiert werden.  
  
 Weitere Informationen finden Sie unter [Initialize a Subscription with a Snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md) und [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
  
