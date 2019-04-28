---
title: Sichern des Verlegers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server replication], publication access list
- publications [SQL Server replication], publication access lists
- publication access list (PAL)
- PAL (publication access list)
- Publishers [SQL Server replication], security
- publications [SQL Server replication], security
ms.assetid: 4513a18d-dd6e-407a-b009-49dc9432ec7e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 201b1496444888b207a1a72be640b9705ff1059d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62960145"
---
# <a name="secure-the-publisher"></a>Sichern des Verlegers
  Die folgenden Replikations-Agents stellen eine Verbindung zum Verleger her:  
  
-   Protokolllese-Agent  
  
-   Momentaufnahme-Agent  
  
-   Warteschlangenlese-Agent  
  
-   Merge-Agent  
  
 Es empfiehlt sich, eine geeignete Anmeldung für diese Agents bereitzustellen, sich an den Grundsatz zu halten, dass nur so viele Rechte erteilt werden sollten, wie unbedingt erforderlich sind, und den Aufbewahrungsort für die Kennwörter zu schützen. Informationen zu den für die einzelnen Agents erforderlichen Berechtigungen finden Sie unter [Replication Agent Security Model](replication-agent-security-model.md).  
  
 Neben der angemessenen Verwaltung von Anmeldungen und Kennwörtern sollten Sie auch über die Rolle der Veröffentlichungszugriffsliste (Publication Access List oder PAL) im Klaren sein. Die PAL wird verwendet, um Anmeldungen den Zugriff auf Veröffentlichungsdaten zu ermöglichen, während gleichzeitig der Ad-hoc-Zugriff auf die Datenbank beim Verleger eingeschränkt wird.  
  
## <a name="publication-access-list"></a>Veröffentlichungszugriffsliste  
 Die PAL ist der primäre Mechanismus für die Sicherung von Veröffentlichungen beim Verleger. Die PAL funktioniert ähnlich wie eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows-Zugriffssteuerungsliste. Wenn Sie eine Veröffentlichung erstellen, wird von der Replikation eine PAL für diese Veröffentlichung erstellt. Die PAL kann so konfiguriert werden, dass Sie eine Liste mit Anmeldungen und Gruppen enthält, denen Zugriff auf die Veröffentlichung gewährt wird. Wenn ein Agent eine Verbindung mit dem Verleger oder Verteiler herstellt und den Zugriff auf eine Veröffentlichung anfordert, werden die Authentifizierungsinformationen in der PAL mit der vom Agent bereitgestellten Verlegeranmeldung verglichen. Dieser Vorgang bietet zusätzliche Sicherheit für den Verleger, da die Anmeldung bei Verleger und Verteiler vor einer Verwendung durch ein Clienttool geschützt ist, das direkt beim Verleger Änderungen ausführen könnte.  
  
> [!NOTE]  
>  Die Replikation erstellt auf dem Verleger eine Rolle für jede Veröffentlichung, um die PAL-Mitgliedschaft durchzusetzen. Für die Mergereplikation weist die Rolle einen Namen im Format **Msmerge_**_\<PublicationID>_ auf, für die Transaktionsreplikation und die Momentaufnahmenreplikation im Format **MSReplPAL_**_\<PublicationDatabaseID>_**_**_\<PublicationID>_.  
  
 Folgende Anmeldungen sind in der PAL standardmäßig enthalten: die Mitglieder der festen **sysadmin** -Serverrolle zum Zeitpunkt der Veröffentlichungserstellung sowie die Anmeldung, die zur Veröffentlichungserstellung verwendet wurde. Standardmäßig können sämtliche Anmeldungen, die Mitglied der festen **sysadmin** -Serverrolle oder der festen **db_owner** -Datenbankrolle in der Veröffentlichungsdatenbank sind, eine Veröffentlichung abonnieren, ohne der PAL explizit hinzugefügt worden zu sein.  
  
 Wenn Sie die PAL verwenden, beachten Sie die folgenden Richtlinien:  
  
-   Sie müssen einem Datenbankbenutzer in der Veröffentlichungsdatenbank die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldung zuordnen, bevor Sie die Anmeldung der PAL hinzufügen.  
  
-   Befolgen Sie das Prinzip der geringsten Rechte, indem Sie den Anmeldungen in der PAL nur die Berechtigungen erteilen, die sie zur Ausführung von Replikationstasks benötigen. Fügen Sie die Anmeldungen keinen festen Datenbank- oder Serverrollen hinzu, die für die Replikation nicht erforderlich sind. Weitere Informationen zu den erforderlichen Berechtigungen finden Sie unter [Replication Agent Security Model](replication-agent-security-model.md) und [Replication Security Best Practices](replication-security-best-practices.md).  
  
-   Wenn ein Remoteverteiler verwendet wird, müssen Konten in der PAL sowohl beim Verleger als auch beim Verteiler verfügbar sein. Das Konto muss entweder ein Domänenkonto oder ein lokales Konto sein, das auf beiden Servern definiert ist. Die den Anmeldenamen zugehörigen Kennwörter müssen übereinstimmen.  
  
-   Wenn die PAL Windows-Konten enthält und von der Domäne Active Directory verwendet wird, muss das Konto, unter dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird, zum Lesen aus Active Directory berechtigt sein. Wenn es hinsichtlich Windows-Konten zu Problemen kommt, stellen Sie sicher, dass das Konto, unter dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird, über ausreichende Berechtigungen verfügt. Weitere Informationen finden Sie in der Windows-Dokumentation.  
  
 Informationen zum Verwalten der Veröffentlichungszugriffsliste finden Sie unter [Verwalten von Anmeldungen in der Veröffentlichungszugriffsliste](manage-logins-in-the-publication-access-list.md).  
  
## <a name="snapshot-agent"></a>Momentaufnahme-Agent  
 Es gibt einen Momentaufnahme-Agent pro Veröffentlichung. Weitere Informationen finden Sie unter [Create a Publication](../publish/create-a-publication.md).  
  
## <a name="ftp-snapshot-delivery"></a>Momentaufnahmeübermittlung per FTP  
 Wenn Sie angeben, dass Momentaufnahmen über eine FTP-Freigabe verfügbar gemacht werden sollen, nicht über eine UNC-Freigabe, müssen Sie beim Konfigurieren des FTP-Zugriffs eine Anmeldung und ein Kennwort angeben. Weitere Informationen finden Sie unter [Übermitteln einer Momentaufnahme über FTP](../publish/deliver-a-snapshot-through-ftp.md).  
  
## <a name="log-reader-agent"></a>Protokolllese-Agent  
 Es gibt einen Protokolllese-Agent für jede Datenbank, die zur Transaktionsreplikation veröffentlicht wird. Weitere Informationen finden Sie unter [Create a Publication](../publish/create-a-publication.md).  
  
## <a name="queue-reader-agent"></a>Warteschlangenlese-Agent  
 Für sämtliche Verleger und Veröffentlichungen (die Abonnements mit verzögerten Updates über eine Warteschlange zulassen), die einem bestimmten Verleger zugeordnet sind, gibt es einen Warteschlangenlese-Agent. Weitere Informationen finden Sie unter [Aktivieren des Aktualisierens von Abonnements für Transaktionsveröffentlichungen](../publish/enable-updating-subscriptions-for-transactional-publications.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &amp;amp;#40;SQL Server-Konfigurations-Manager&amp;amp;#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)   
 [Replication Security Best Practices](replication-security-best-practices.md)   
 [Sicherheit von SQL Server-Replikation](view-and-modify-replication-security-settings.md)  
  
  
