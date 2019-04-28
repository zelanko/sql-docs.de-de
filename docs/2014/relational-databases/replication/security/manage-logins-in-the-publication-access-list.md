---
title: Verwalten von Anmeldungen in der Veröffentlichungszugriffsliste| Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server replication], publication access list
- publications [SQL Server replication], publication access lists
- publication access list (PAL)
- PAL (publication access list)
- logins [SQL Server replication], managing
ms.assetid: fceb216b-0b18-4e3b-8ae0-13e35920dcbc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 966b8a03d10bb8e87950e19e3e099954e8aaad8f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62960954"
---
# <a name="manage-logins-in-the-publication-access-list"></a>Verwalten von Anmeldungen in der Veröffentlichungszugriffsliste
  In diesem Thema wird beschrieben, wie Anmeldungen in der Veröffentlichungszugriffsliste in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]verwaltet werden. Der Zugriff auf eine Veröffentlichung wird von der Veröffentlichungszugriffsliste (Publication Access List, PAL) gesteuert. Anmeldungen und Gruppen können hinzugefügt und aus PAL entfernt werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Erforderliche Komponenten](#Prerequisites)  
  
-   **So verwalten Sie Anmeldungen in der Veröffentlichungszugriffsliste mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   Sie müssen einem Datenbankbenutzer in der Veröffentlichungsdatenbank die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldung zuordnen, bevor Sie die Anmeldung PAL hinzufügen.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Sie verwenden die Veröffentlichungszugriffsliste (Publication Access List, PAL) auf der Seite **Veröffentlichungszugriffsliste** des Dialogfelds **Veröffentlichungseigenschaften – \<Veröffentlichung>** zum Verwalten der Anmeldenamen. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [Anzeigen und Ändern von Veröffentlichungseigenschaften](../publish/view-and-modify-publication-properties.md).  
  
#### <a name="to-manage-logins-in-the-pal"></a>So verwalten Sie Anmeldenamen in der Veröffentlichungszugriffsliste  
  
1.  Die Seite **Veröffentlichungszugriffsliste** des Dialogfelds **Veröffentlichungseigenschaften – \<Veröffentlichung>** enthält die Schaltflächen **Hinzufügen**, **Entfernen** und **Alle entfernen**, mit denen Sie Benutzer (Anmeldenamen) und Gruppen in die Veröffentlichungszugriffsliste aufnehmen bzw. entfernen können. Sie dürfen **distributor_admin** nicht aus der PAL entfernen. Dieses Konto wird für die Replikation verwendet.  
  
    > [!NOTE]  
    >  Wenn ein Remoteverteiler verwendet wird, müssen Konten in der PAL sowohl beim Verleger als auch beim Verteiler verfügbar sein. Das Konto muss entweder ein Domänenkonto oder ein lokales Konto sein, das auf beiden Servern definiert ist. Die den Anmeldenamen zugehörigen Kennwörter müssen übereinstimmen.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-view-groups-and-logins-that-belong-to-the-pal"></a>So zeigen Sie Gruppen und Anmeldungen an, die zur PAL gehören  
  
1.  Führen Sie beim Verleger für die Veröffentlichungsdatenbank [sp_help_publication_access](/sql/relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql)aus. Geben Sie für **@publication**den Veröffentlichungsnamen an. Dadurch werden Informationen über die Gruppen und Anmeldungen in der PAL angezeigt.  
  
#### <a name="to-add-groups-and-logins-to-the-pal"></a>So fügen Sie der PAL Gruppen und Anmeldungen hinzu  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_grant_publication_access](/sql/relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql)aus. Geben Sie für **@publication**an. Geben Sie den Namen der Anmeldung oder Gruppe, die hinzugefügt wird, für **@login**an.  
  
#### <a name="to-remove-groups-and-logins-from-the-pal"></a>So entfernen Sie Gruppen und Anmeldungen aus der PAL  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_revoke_publication_access](/sql/relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql)aus. Geben Sie für **@publication**an. Geben Sie den Namen der Anmeldung oder Gruppe, die hinzugefügt wird, für **@login**an.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitsmodell des Replikations-Agents](replication-agent-security-model.md)   
 [Sichern einer Replikationstopologie](view-and-modify-replication-security-settings.md)   
 [Sichern des Verlegers](secure-the-publisher.md)  
  
  
