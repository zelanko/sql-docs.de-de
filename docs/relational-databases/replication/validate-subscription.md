---
description: Abonnement überprüfen
title: Abonnement überprüfen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.validate.validateandresynch.f1
helpviewer_keywords:
- Validate Subscription dialog box
ms.assetid: 74bdf5e1-b886-4284-b5fb-332bf79ae083
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016
ms.openlocfilehash: e66d2b6c088126285f52b462ec2bf9f125f81cc9
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97468691"
---
# <a name="validate-subscription"></a>Abonnement überprüfen
[!INCLUDE[sql-asdb](../../includes/applies-to-version/sql-asdb.md)]
  Im Dialogfeld **Abonnements überprüfen** können Sie angeben, dass ein Abonnement für eine Mergeveröffentlichung überprüft werden soll, sobald der Merge-Agent für das Abonnement das nächste Mal ausgeführt wird. Die Ergebnisse der Überprüfung werden im Replikationsmonitor angezeigt. Weitere Informationen finden Sie unter [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  
  
 Wenn Sie in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] zunächst mit der rechten Maustaste auf eine Veröffentlichung und dann auf **Alle Abonnements überprüfen** klicken, können Sie auch alle Abonnements einer Mergeveröffentlichung überprüfen.  

[!INCLUDE[azure-sql-db-replication-supportability-note](../../includes/azure-sql-db-replication-supportability-note.md)]
  
## <a name="options"></a>Optionen  
 **Datum der letzten versuchten Überprüfung**  
 Das Datum der letzten Merge-Agent-Sitzung, bei der Abonnements überprüft wurden. Der Erfolg der Überprüfung ist dabei nicht entscheidend.  
  
 **Datum der letzten erfolgreichen Überprüfung**  
 Das Datum der letzten Merge-Agent-Sitzung, bei der Abonnements erfolgreich überprüft wurden.  
  
 **Dieses Abonnement überprüfen**  
 Wählen Sie diese Option aus, um das Abonnement zu überprüfen.  
  
 **Optionen**  
 Klicken Sie auf diese Option, um auf das Dialogfeld **Optionen für die Abonnementüberprüfung** zuzugreifen, in dem Sie angeben können, ob die Zeilenanzahlüberprüfung oder die binäre Prüfsummenüberprüfung verwendet werden soll.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überprüfen von replizierten Daten](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
