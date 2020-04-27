---
title: Agentsicherheit (Assistent für neue Veröffentlichung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.agentsecurity.articles.f1
ms.assetid: 05ae44df-8e9f-46ea-95f6-972ad109c6c0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 555aa4e49887000354e5d31ff5d039a5f0ac75eb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63259162"
---
# <a name="agent-security-new-publication-wizard"></a>Agentsicherheit (Assistent für neue Veröffentlichung)
  Mithilfe der Seite **Agentsicherheit** können Sie die Konten angeben, unter denen die folgenden Agents ausgeführt werden und Verbindungen mit den Computern in einer Replikationstopologie herstellen:  
  
-   Der Momentaufnahme-Agent für alle Veröffentlichungen.  
  
-   Der Protokolllese-Agent für alle Transaktionsveröffentlichungen.  
  
-   Der Warteschlangenlese-Agent für Transaktionsveröffentlichungen, die Abonnements mit Aktualisierung gestatten. Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agentauftrag wird erstellt, wenn Sie auf der Seite **Veröffentlichungstyp** die Option **Transaktionsveröffentlichung mit aktualisierbaren Abonnements** angegeben haben. Der Typ Ihrer aktualisierbaren Abonnements spielt keine Rolle. Weitere Informationen zu aktualisierbaren Abonnements finden Sie unter [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 Weitere Informationen zu den für Agents erforderlichen Berechtigungen und zu bewährten Methoden der Replikationssicherheit finden Sie unter [Replication Agent Security Model](security/replication-agent-security-model.md) und [Replication Security Best Practices](security/replication-security-best-practices.md).  
  
## <a name="options"></a>Tastatur  
 **Momentaufnahme-Agent**  
 Wird für alle Veröffentlichungen angezeigt. Klicken Sie auf **Sicherheitseinstellungen** , um die Sicherheitseinstellungen im Dialogfeld **Sicherheit für den Momentaufnahme-Agent** anzugeben.  
  
 Klicken Sie im Dialogfeld **Sicherheit für den Momentaufnahme-Agent** auf **Hilfe** , um weitere Informationen zu den Berechtigungen zu erhalten, die für die vom Momentaufnahme-Agent verwendeten Konten erforderlich sind.  
  
 **Protokolllese-Agent**  
 Wird für alle Transaktionsveröffentlichungen angezeigt. Klicken Sie auf **Sicherheitseinstellungen** , um die Sicherheitseinstellungen im Dialogfeld **Sicherheit für den Protokolllese-Agent** anzugeben.  
  
 Klicken Sie im Dialogfeld **Sicherheit für den Protokolllese-Agent** auf **Hilfe** , um weitere Informationen zu den Berechtigungen zu erhalten, die für die vom Protokolllese-Agent verwendeten Konten erforderlich sind.  
  
> [!NOTE]  
>  Es gibt einen Protokolllese-Agent für jede Datenbank, die mithilfe der Transaktionsreplikation veröffentlicht wird. Wenn bereits eine Transaktionsveröffentlichung in der Datenbank vorhanden ist, sind die Sicherheitseinstellungen schreibgeschützt. Sie können die Einstellungen im Dialogfeld **Veröffentlichungseigenschaften** ändern, diese Änderungen wirken sich jedoch auf alle Transaktionsveröffentlichungen in der Datenbank aus.  
  
 **Warteschlangenlese-Agent**  
 Wird für Momentaufnahme- oder Transaktionsveröffentlichungen angezeigt, die aktualisierbare Abonnements zulassen. Klicken Sie auf **Sicherheitseinstellungen** , um die Sicherheitseinstellungen im Dialogfeld **Sicherheit für den Warteschlangenlese-Agent** anzugeben. Bei Abschluss dieses Assistenten wird ein Auftrag des Warteschlangenlese-Agents erstellt, unabhängig davon, ob Sie Abonnements mit verzögertem Update über eine Warteschlange erstellen. Wenn Sie keine Abonnements mit verzögertem Update über eine Warteschlange erstellen möchten, können Sie den Auftrag deaktivieren. Mit der rechten Maustaste klicken Sie auf den Auftrag (mit dem Namen in der Form: *[\<Publisher >].\< ganze Zahl >* .) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **Aufträge** Ordner, und klicken Sie dann auf **Deaktivieren**  
  
 Klicken Sie im Dialogfeld **Sicherheit für den Warteschlangenlese-Agent** auf **Hilfe** , um weitere Informationen zu den Berechtigungen zu erhalten, die für die vom Warteschlangenlese-Agent verwendeten Konten erforderlich sind.  
  
> [!NOTE]  
>  Für jede Verteilungsdatenbank (und alle dazugehörigen Verleger) gibt es einen Warteschlangenlese-Agent. Wenn eine Transaktionsveröffentlichung, die Abonnements mit verzögertem Update über eine Warteschlange gestattet, bereits auf einem der Verleger vorhanden ist, die eine bestimmte Verteilungsdatenbank verwenden, sind die Sicherheitseinstellungen schreibgeschützt. Sie können das Konto, unter dem der Warteschlangenlese-Agent ausgeführt wird und Verbindungen herstellt, im Dialogfeld **Verteilereigenschaften** ändern. Die Änderungen wirken sich jedoch auf alle Veröffentlichungen aller Verleger aus, die die Verteilungsdatenbank verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Publication](publish/create-a-publication.md)   
 [Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md)   
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](view-and-modify-distributor-and-publisher-properties.md)   
 [Anzeigen und Ändern von Veröffentlichungseigenschaften](publish/view-and-modify-publication-properties.md)   
 [Verwalten von Anmeldungen und Kenn Wörtern in der Replikation](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [Veröffentlichen von Daten und Datenbankobjekten](publish/publish-data-and-database-objects.md)   
 [Übersicht über Replikations-Agents](agents/replication-agents-overview.md)  
  
  
