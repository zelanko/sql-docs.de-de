---
description: Sicherheit für den Warteschlangenlese-Agent
title: Sicherheit für den Warteschlangenlese-Agent | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.security.QRA.f1
helpviewer_keywords:
- Queue Reader Agent Security dialog box
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dc5a8ff1f69f26fc7925a2314151e9437ffefc65
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88406246"
---
# <a name="queue-reader-agent-security"></a>Sicherheit für den Warteschlangenlese-Agent
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
   Im Dialogfeld **Sicherheit für den Warteschlangenlese-Agent** können Sie das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto angeben, unter dem der Warteschlangenlese-Agent ausgeführt wird und lokale Verbindungen mit dem Verteiler herstellt. Der Agent stellt mithilfe des im Dialogfeld **Verlegereigenschaften** (über das Dialogfeld **Verteilereigenschaften** verfügbar) angegebenen Kontos die Verbindung zum Verleger her. Der Agent stellt für das Abonnement mithilfe desselben Kontexts wie der Verteilungs-Agent die Verbindung mit dem Abonnenten her. Weitere Informationen finden Sie unter [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Das Konto muss für das angegebene Kennwort gültig sein. Konten und Kennwörter werden erst bei der Ausführung eines Agents überprüft.  
  
## <a name="options"></a>Tastatur  
 **Prozesskonto**  
 Geben Sie das Windows-Konto ein, unter dem der Warteschlangenlese-Agent auf dem Verteiler ausgeführt wird. Das angegebene Windows-Konto muss mindestens ein Mitglied der festen Datenbankrolle **db_owner** in der Verteilungsdatenbank sein.  
  
 **Kennwort** und **Kennwort bestätigen**  
 In diese Felder geben Sie das Kennwort für das Windows-Konto ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Identität und Zugriffssteuerung (Replikation)](../../relational-databases/replication/security/identity-and-access-control-replication.md)   
 [Sicherheitsmodell des Replikations-Agents](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Replikations-Agents (Übersicht)](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Bewährte Methoden für die Replikationssicherheit](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
