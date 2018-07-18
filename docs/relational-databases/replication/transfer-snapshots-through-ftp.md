---
title: Übertragen von Momentaufnahmen über FTP | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], FTP snapshots
- FTP snapshots [SQL Server replication]
- snapshot replication [SQL Server], FTP
ms.assetid: 55c30791-cd2a-420b-8ba7-5700e005cb45
caps.latest.revision: 40
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 60eb8d1ef0186ab3fba890fb2ba2f44d514ddcd1
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37356342"
---
# <a name="transfer-snapshots-through-ftp"></a>Übertragen von Momentaufnahmen über FTP
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Standardmäßig werden Momentaufnahmen in Ordnern gespeichert, die als im UNC-Format (Universal Naming Convention) angegebene Dateifreigaben definiert sind. Bei der Replikation haben Sie ebenfalls die Möglichkeit, FTP-Freigaben (FTP, File Transfer Protocol) anstelle der UNC-Freigaben anzugeben. Dazu müssen Sie einen FTP-Server und anschließend eine Veröffentlichung sowie mindestens ein Abonnement über FTP konfigurieren. Informationen dazu, wie ein FTP-Server konfiguriert wird, finden Sie in der Internetinformationsdienste (IIS)-Dokumentation. Wenn Sie FTP-Informationen für eine Veröffentlichung angeben, verwenden die Abonnements dieser Veröffentlichung standardmäßig FTP. FTP wird nur zur Websynchronisierung verwendet, wenn der Computer, auf dem IIS (Internet Information Services, Internetinformationsdienste) ausgeführt wird, vom Verteiler durch eine Firewall getrennt ist. In diesem Fall kann die Momentaufnahme über FTP vom Verteiler an den Computer, auf dem IIS ausgeführt wird, gesendet werden. (Zur Übertragung der Momentaufnahme an den Abonnenten wird immer HTTPS verwendet.)  
  
> [!IMPORTANT]  
>  Es wird empfohlen, vorzugsweise die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung und eine UNC-Freigabe statt einer FTP-Freigabe zu verwenden, da FTP-Kennwörter gespeichert werden müssen, und das Kennwort vom Abonnenten oder von dem Computer, auf dem IIS bei der Websynchronisierung ausgeführt wird, als unverschlüsselter Text an den FTP-Server gesendet wird. Außerdem ist es bei der Übertragung über FTP nicht möglich, sicherzustellen, dass ein Abonnent einer gefilterten Mergeveröffentlichung ausschließlich auf die Momentaufnahmen seiner Datenpartition zugreifen kann, da ein einziges Konto den Zugriff auf die gesamte Momentaufnahme-Freigabe kontrolliert.  
  
 Informationen zum Übermitteln einer Momentaufnahme über FTP finden Sie unter [Deliver a Snapshot Through FTP](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Websynchronisierung für die Mergereplikation](../../relational-databases/replication/web-synchronization-for-merge-replication.md)   
 [Initialisieren eines Abonnements mit einer Momentaufnahme](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Momentaufnahmeoptionen](../../relational-databases/replication/snapshot-options.md)  
  
  
