---
title: SQL Server-Replikation Verlegereigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distpubproperties.f1
- sql12.rep.configdistwizard.pubproperties.general.f1
- sql12.rep.configdistwizard.pubproperties.pubdb.f1
- sql12.rep.configdistwizard.pubproperties.subscribers.f1
ms.assetid: 98df1aea-0406-40bf-a917-4bd80464125c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2ea467b00223e31ec7672d4d54a49150cf05368c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63261975"
---
# <a name="sql-server-replication-publisher-properties"></a>SQL Server-Replikation Publisher-Eigenschaften
  Dieser Abschnitt enthält Informationen zu den Verlegereigenschaften, die auf dem Verteiler und Verleger verfügbar sind. 

## <a name="general"></a>Allgemein  
  Die Seite **Allgemein** des Dialogfelds **Verlegereigenschaften** zeigt schreibgeschützte Informationen zu dem Verteiler und der Verteilungsdatenbank an, die vom Verleger verwendet werden. So ändern Sie den Verteiler oder die Verteilungsdatenbank für einen Verleger:  
  
1.  Deaktivieren Sie die Veröffentlichung auf dem Verleger. Weitere Informationen finden Sie unter [Deaktivieren der Veröffentlichung und Verteilung](disable-publishing-and-distribution.md).    
2.  Konfigurieren Sie die Veröffentlichung und die Verteilung neu. Weitere Informationen finden Sie unter [Configure Publishing and Distribution](configure-publishing-and-distribution.md).  

## <a name="distributor"></a>Verteiler
  Mithilfe des Dialogfelds **Verlegereigenschaften** können Sie mit der Beziehung zwischen dem Verleger und dem Verteiler verknüpfte Eigenschaften anzeigen und ändern.  
  
### <a name="options"></a>Optionen  
 **Agentverbindung mit dem Verleger**  
 Geben Sie den Kontext an, in dem die folgenden Agenten Verbindungen vom Verteiler zum Verleger herstellen können:  
  
-   Der Warteschlangenlese-Agent für Transaktionsveröffentlichungen, die Abonnements mit verzögertem Update über eine Warteschlange gestatten.  
  
-   Der Momentaufnahme-Agent und der Protokolllese-Agent für Oracle-Veröffentlichungen.  
  
 Wählen Sie **Identität des Agentprozesskontos annehmen** aus, um Verbindungen mit dem Verleger mithilfe des Kontexts des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Kontos herzustellen, unter dem diese Agents ausgeführt werden, oder geben Sie **SQL Server-Authentifizierung**an, und geben Sie dann einen Wert für **Benutzername** und **Kennwort**ein. Es wird empfohlen, **Identität des Agentprozesskontos annehmen**auszuwählen. Weitere Informationen zur Agentsicherheit finden Sie unter [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
 Die Windows-Konten, unter denen diese Agents ausgeführt werden, werden im Assistenten für neue Veröffentlichung angegeben. Diese Konten können geändert werden:  
  
-   Im Dialogfeld **Verteilereigenschaften** für den Warteschlangenlese-Agent.  
  
-   Im Dialogfeld **Veröffentlichungseigenschaften** für den Momentaufnahme-Agent und den Protokolllese-Agent.  
  
 **Sonstiges**  
 Die Eigenschaften **Verlegertyp** und **Name der Verteilungsdatenbank** sind schreibgeschützt. Die Eigenschaft **Standardmomentaufnahmeordner** kann geändert werden. Weitere Informationen zum Momentaufnahmeordner finden Sie unter [Sichern des Momentaufnahmeordners](security/secure-the-snapshot-folder.md).  
  

## <a name="publication-databases"></a>Veröffentlichungsdatenbanken
  Mithilfe der Seite **Veröffentlichungsdatenbanken** des Dialogfelds **Verlegereigenschaften** können Benutzer mit der festen Serverrolle **sysadmin** Datenbanken für die Replikation aktivieren. Das Aktivieren der Datenbank führt nicht zur Veröffentlichung dieser Datenbank. Vielmehr ermöglicht dies allen Benutzern mit der festen Datenbankrolle **db_owner** für diese Datenbank eine oder mehrere Veröffentlichungen auf dieser Datenbank zu erstellen.  
  
### <a name="options"></a>Optionen  
 **Transaktion**  
 Aktivieren Sie dieses Kontrollkästchen, um es Benutzern mit der festen Datenbankrolle **db_owner** zu ermöglichen, Momentaufnahme- oder Transaktionsveröffentlichungen in der Datenbank zu erstellen. 
  
 **Merge**  
 Aktivieren Sie dieses Kontrollkästchen, um es Benutzern mit der festen Datenbankrolle **db_owner** zu ermöglichen, Mergeveröffentlichungen in der Datenbank zu erstellen.  

## <a name="subscribers"></a>Abonnenten

  Die Seite **Abonnenten** des Dialogfelds **Verlegereigenschaften** wird für Verleger verwendet, auf denen Versionen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]ausgeführt werden. Mithilfe dieser Seite können Sie es Abonnenten ermöglichen, Daten von Veröffentlichungen auf diesem Verleger zu empfangen. Wenn Sie einem Abonnenten ermöglichen, Daten von diesem Verleger zu empfangen, werden dadurch keine Abonnements für Veröffentlichungen auf diesem Verleger erstellt. Zum Erstellen eines Abonnements müssen Sie den Assistenten für neue Abonnements verwenden.  
  
### <a name="options"></a>Optionen  
 **Abonnenten**  
 Das Eigenschaftenraster **Abonnenten** zeigt Abonnenten an, die zum Empfangen von Daten von Veröffentlichungen auf diesem Verleger aktiviert sind. Klicken Sie neben einem Abonnenten auf die Eigenschaftenschaltfläche (die Schaltfläche mit den **drei Punkten**), um zusätzliche Eigenschaften anzuzeigen und festzulegen.  
  
 **Hinzufügen**  
 Klicken Sie auf **Hinzufügen** , um einen Abonnenten hinzuzufügen, und dann auf **SQL Server-Abonnenten hinzufügen** oder **Nicht-SQL Server-Abonnenten hinzufügen**.  

## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](view-and-modify-distributor-and-publisher-properties.md)   

  
  
