---
title: Anmeldename für aktualisierbare Abonnements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.updatablesubscriptionslogin.f1
ms.assetid: 301ea227-0455-40ba-9009-d38f8676b325
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2ccf1a79b2dc27bbc49628d11a0c6fb0cf0e4e50
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52816622"
---
# <a name="login-for-updatable-subscriptions"></a>Anmeldename für aktualisierbare Abonnements
  Wenn Sie im Assistenten auf der Seite **Aktualisierbare Abonnements** die Option **Replizieren** ausgewählt haben, müssen Sie auf dem Abonnenten ein Konto angeben, unter dem die Verbindungen mit dem Verleger für die sofort aktualisierbaren Abonnements hergestellt werden. Die Verbindungen werden durch die Trigger verwendet, die auf dem Abonnenten ausgelöst werden und die Änderungen zum Verleger weitergeben. Das Konto wird auch dann benötigt, wenn Sie auf der Seite **Aktualisierbare Abonnements** die Option **Änderungen in die Warteschlange einreihen und Commit baldmöglichst ausführen** ausgewählt haben, da die in die Warteschlange eingereihten Updates durch den Assistenten für neue Abonnements standardmäßig so konfiguriert werden, dass die Möglichkeit besteht, zum sofortigen Update zu wechseln.  
  
> [!IMPORTANT]  
>  Dem für die Verbindung angegebenen Konto sollten nur die Berechtigung zum Einfügen, Aktualisieren und Löschen der Daten in den durch die Replikation in der Veröffentlichungsdatenbank erstellten Sichten erteilt werden; darüber hinaus sollte das Konto über keine weiteren Berechtigungen verfügen. Erteilen Sie dem von Ihnen auf den einzelnen Abonnenten konfigurierten Konto Berechtigungen für Sichten in der Veröffentlichungsdatenbank, deren Namen das Format **syncobj_***\<Hexadezimalzahl>* aufweisen.  
  
 Für den Typ der Verbindung gibt es drei Optionen:  
  
-   Ein vordefinierter Verbindungsserver oder Remoteserver.  
  
-   Ein durch die Replikation erstellter Verbindungsserver. Die Verbindung wird mit den Anmeldeinformationen hergestellt, die Sie im Assistenten angeben.  
  
-   Ein durch die Replikation erstellter Verbindungsserver. Die Verbindung wird mit den Anmeldeinformationen des Benutzers hergestellt, der die Änderung auf dem Abonnenten vornimmt.  
  
 Die ersten beiden Optionen können im Assistenten angegeben werden. Die letzte Option kann nur mithilfe von [sp_link_publication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) angegeben werden. Geben Sie für den Parameter **@security_mode** den Wert **1** an.  
  
## <a name="options"></a>Optionen  
 **Erstellen Sie einen Verbindungsserver, der die Verbindung mithilfe des folgenden Anmeldenamens für die SQL Server-Authentifizierung herstellt:**  
 Durch die Replikation wird ein Verbindungsserver mithilfe der in den Feldern **Anmeldename** und **Kennwort** angegebenen Anmeldeinformationen erstellt.  
  
 **Anmeldename**  
 Geben Sie einen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldenamen ein, der nur die in diesem Thema beschriebenen Berechtigungen aufweist.  
  
 **Kennwort**  
 Geben Sie ein sicheres Kennwort für den in **Anmeldename**angegebenen Anmeldenamen ein.  
  
 **Kennwort bestätigen**  
 Geben Sie das Kennwort zur Bestätigung der fehlerfreien Eingabe erneut ein.  
  
 **Vordefinierten Verbindungsserver oder Remoteserver verwenden**  
 Bei dieser Option ist ein bereits von Ihnen definierter Verbindungsserver oder Remoteserver erforderlich. Weitere Informationen finden Sie unter [Verbindungsserver &amp;#40;Datenbank-Engine&amp;#41;](../linked-servers/linked-servers-database-engine.md) und [Remoteserver](../../database-engine/configure-windows/remote-servers.md). Stellen Sie sicher, dass der für den Verbindungsserver oder Remoteserver verwendete Anmeldename ein sicheres Kennwort sowie ausschließlich die in diesem Thema beschriebenen Berechtigungen aufweist.  
  
## <a name="see-also"></a>Siehe auch  
 [Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md)   
 [Anzeigen und Ändern von Replikationssicherheitseinstellungen](security/view-and-modify-replication-security-settings.md)   
 [Aktualisierbare Abonnements für die Transaktionsreplikation](transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)  
  
  
