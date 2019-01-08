---
title: Sichern des Momentaufnahmeordners | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], security
ms.assetid: 3cd877d1-ffb8-48fd-a72b-98eb948aad27
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cb3aa18f17219f46bc5ce6f3d25af7d4bd29c4d9
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52753952"
---
# <a name="secure-the-snapshot-folder"></a>Sichern des Momentaufnahmeordners
  Der Momentaufnahmeordner ist ein Verzeichnis, in dem Momentaufnahmedateien gespeichert werden. Es empfiehlt sich, dieses Verzeichnis zum Speichern von Momentaufnahmen zu reservieren. Gewähren Sie dem Momentaufnahme-Agent Schreibzugriff auf den Ordner, und stellen Sie sicher, dass nur das Windows-Konto Leseberechtigung erhält, das der Merge-Agent bzw. der Verteilungs-Agent für den Zugriff auf den Ordner verwendet. Das dem Agent zugeordnete Windows-Konto muss ein Domänenkonto sein, damit auf den Momentaufnahmeordner zugegriffen werden kann, der sich auf einem Remotecomputer befindet.  
  
> [!NOTE]  
>  Die Benutzerkontensteuerung (User Account Control, UAC) unterstützt Administratoren bei der Verwaltung erhöhter Benutzerrechte (auch *Privilegien*genannt). Bei der Ausführung unter Betriebssystemen mit aktivierter Benutzerkontensteuerung nutzen Administratoren keine Administratorrechte. Sie führen stattdessen die meisten Aktionen als Standardbenutzer (nicht als Administrator) aus und nehmen ihre Administratorrechte nur bei Bedarf vorübergehend in Anspruch. Durch die Benutzerkontensteuerung wird möglicherweise der Administratorzugriff auf die Momentaufnahmefreigabe verhindert. Sie müssen daher den vom Momentaufnahme-Agent, Verteilungs-Agent und Merge-Agent verwendeten Windows-Konten explizit Berechtigungen für die Momentaufnahmefreigabe erteilen. Dies ist auch dann erforderlich, wenn die Windows-Konten Mitglieder der Administratorengruppe sind.  
  
 Wenn Sie im Verteilungskonfigurations-Assistenten oder den Assistenten für neue Veröffentlichung einen Verteiler konfigurieren, wird standardmäßig der momentaufnahmeordner in einen lokalen Pfad: X:\Program Files\Microsoft SQL Server\\*\<Instanz >* \MSSQL\ReplData. Wenn Sie einen Remoteverteiler oder Pullabonnements verwenden, müssen Sie eine UNC-Netzwerkfreigabe (z.B. \\\\<*Computername>* \Momentaufnahme) anstelle eines lokalen Pfads angeben.  
  
 Wenn Sie Zugriffsberechtigungen für den Momentaufnahmeordner erteilen, müssen Sie sie entsprechend der Zugriffsweise für den Ordner festlegen. Unter [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2003 werden die folgenden Registerkarten des Dialogfelds verwendet:  
  
-   Beim Angeben eines lokalen Pfads erteilen Sie die Berechtigungen für den Ordner im Dialogfeld **Eigenschaften** über die Registerkarte **Sicherheit** .  
  
-   Beim Angeben einer Netzwerkfreigabe erteilen Sie die Berechtigungen für den Ordner im Dialogfeld **Eigenschaften** über die Registerkarte **Freigabe** .  
  
    > [!NOTE]  
    >  Wenn der Replikations-Agent auf dem Verteiler ausgeführt wird, verwenden Sie im Dialogfeld **Eigenschaften** die Registerkarte **Sicherheit** für den Ordner, um dem Windows-Konto, unter dem der Agent ausgeführt wird, die Berechtigungen zu erteilen. Führen Sie diesen Vorgang auch bei Verwendung einer Netzwerkfreigabe aus. Dies gilt für den Merge-Agent und den Verteilungs-Agent bei einem Pushabonnement und für den Momentaufnahme-Agent, wenn sich der Verleger und der Verteiler auf demselben Computer befinden.  
  
 Weitere Informationen zum Festlegen der Berechtigungen für lokale Pfade und Netzwerkfreigaben finden Sie in der Windows-Dokumentation.  
  
> [!NOTE]  
>  Wenn eine Veröffentlichung gelöscht wird, wird bei der Replikation versucht, den Momentaufnahmeordner im Sicherheitskontext des Kontos für den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienst zu entfernen. Falls dieses Konto nicht über ausreichende Berechtigungen verfügt, melden Sie sich mit einem anderen Konto mit ausreichenden Berechtigungen an, und entfernen Sie den Ordner manuell. Zum Entfernen eines Ordners ist die Berechtigung **Ändern** erforderlich, wenn es sich um einen lokalen Pfad handelt. Wenn es sich bei dem Ordner um einen Netzwerkpfad handelt, ist die Berechtigung **Vollzugriff** erforderlich.  
  
## <a name="delivering-snapshots-through-ftp"></a>Übermitteln von Momentaufnahmen über FTP  
 Als bewährte Sicherheitsmethode empfiehlt es sich, Momentaufnahmen in einer UNC-Freigabe zu speichern, sie können jedoch auch in einer FTP-Freigabe gespeichert und anschließend über FTP an einen Abonnenten übermittelt werden. Stellen Sie bei der Konfiguration des FTP-Servers sicher, dass das virtuelle Verzeichnis eine zugrunde liegende UNC-Freigabe verfügbar macht, die dem Momentaufnahme-Agent Schreibzugriff auf die Veröffentlichung gewährt.  
  
 Um einen Abonnenten so zu konfigurieren, dass er die Momentaufnahme über FTP abruft, richten Sie zuerst einen FTP-Server mit einem FTP-Benutzernamen und -Kennwort ein, der den Abonnenten Lese-(bzw. "abrufen"-)Zugriff zum Herunterladen der Momentaufnahmedateien gewährt.  
  
 Informationen zum Übermitteln einer Momentaufnahme über FTP finden Sie unter [Übermitteln einer Momentaufnahme über FTP](../publish/deliver-a-snapshot-through-ftp.md).  
  
 Informationen zum Festlegen und Ändern des Kennworts für den Zugriff auf Momentaufnahmen über FTP finden Sie im Abschnitt "Momentaufnahmeübermittlung per FTP" im Thema [Secure the Publisher](secure-the-publisher.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Alternative Speicherorte für Momentaufnahmeordner](../alternate-snapshot-folder-locations.md)   
 [Initialisieren eines Abonnements mit einer Momentaufnahme](../initialize-a-subscription-with-a-snapshot.md)   
 [Replication Security Best Practices](replication-security-best-practices.md)   
 [Sicherheit und Schutz &#40;Replikation&#41;](security-and-protection-replication.md)   
 [Übertragen von Momentaufnahmen über FTP](../transfer-snapshots-through-ftp.md)  
  
  
