---
title: 'Lektion 3: Konfigurieren der Verteilung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f248984a-0b59-4c2f-a56d-31f8dafe72b5
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 8d873d3664c88963b17550734b488e6872a9cc84
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62721097"
---
# <a name="lesson-3-configuring-distribution"></a>Lektion 3: Konfigurieren der Verteilung
  In dieser Lektion konfigurieren Sie die Verteilung auf dem Verleger und legen die erforderlichen Berechtigungen für die Verteilungs- und Veröffentlichungsdatenbanken fest. Wenn der Verteiler bereits konfiguriert wurde, müssen die Veröffentlichung und die Verteilung erst deaktiviert werden, bevor Sie mit dieser Lektion beginnen. Führen Sie diese Lektion nicht aus, wenn Sie eine vorhandene Replikationstopologie beibehalten müssen.  
  
 Das Konfigurieren eines Verlegers mit einem Remoteverteiler wird in diesem Lernprogramm nicht behandelt.  
  
### <a name="configuring-distribution-at-the-publisher"></a>Konfigurieren der Verteilung auf dem Verleger  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Ordner **Replikation** , und klicken Sie anschließend auf **Verteilung konfigurieren**.  
  
    > [!NOTE]  
    >  Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]localhost** anstelle des tatsächlichen Servernamens verwendet haben, um eine Verbindung mit ** herzustellen, werden Sie in einer Warnmeldung darauf hingewiesen, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht in der Lage ist, eine Verbindung mit dem Server **"localhost"** herzustellen. Klicken Sie im Warnungsdialogfeld auf **OK** . Ändern Sie im Dialogfeld **Verbindung mit Server herstellen** die Angabe für **Servername** von **localhost** in den Namen des Servers. Klicken Sie auf **Verbinden**.  
  
     Der Verteilungskonfigurations-Assistent wird gestartet.  
  
3.  Wählen Sie auf der Seite **Verteiler** die Option **"**_\<Servername>_ **" als seinen eigenen Verteiler aus. SQL Server erstellt eine Verteilungs Datenbank und ein Protokoll**, und klicken Sie dann auf **weiter**.  
  
4.  Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht ausgeführt wird, wählen Sie auf der Seite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**Agent-Start** die Option **Ja**, den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zum automatischen Starten konfigurieren. Klicken Sie auf **Weiter**.  
  
5.  Geben ** \\ **Sie \< _Machine_Name>_ **\repldata** im Textfeld **Momentaufnahme Ordner** ein \<, in dem *Machine_Name>* der Name des Verlegers ist, und klicken Sie dann auf **weiter**.  
  
6.  Übernehmen Sie die Standardwerte auf den restlichen Seiten des Assistenten.  
  
7.  Klicken Sie auf **Fertig stellen** , um die Verteilung zu aktivieren.  
  
### <a name="setting-database-permissions-at-the-publisher"></a>Festlegen der Datenbankberechtigungen auf dem Verleger  
  
1.  Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]den Knoten **Sicherheit**, klicken Sie mit der rechten Maustaste auf **Anmeldungen**, und wählen Sie anschließend **Neue Anmeldung**aus.  
  
2.  Klicken Sie auf der Seite **Allgemein** auf **Suchen**, \<geben Sie _Machine_Name>_ **\ repl_snapshot** im Feld **Geben Sie die zu ausgewäfenden Objektnamen** ein ein, wobei \< *Machine_Name>* der Name des lokalen Verleger Servers ist. Klicken Sie auf **Namen überprüfen**, und klicken Sie dann auf **OK**.  
  
3.  Wählen Sie auf der Seite **Benutzerzuordnung** in der Liste **Benutzer, die dieser Anmeldung zugeordnet sind** sowohl die **Verteilungs** - als auch die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank aus.  
  
     Wählen Sie in der Liste **Daten bankrollen Mitgliedschaft** die `db_owner` Rolle für den Anmelde Namen für beide Datenbanken aus.  
  
4.  Klicken Sie auf **OK** , um die Anmeldung zu erstellen.  
  
5.  Wiederholen Sie die Schritte 1 bis 4, um eine Anmeldung für das lokale Konto repl_logreader zu erstellen. Diese Anmeldung muss auch Benutzern zugeordnet werden, die Mitglieder der `db_owner` Fixed-Daten Bank Rolle in den Datenbanken **Distribution** und **AdventureWorks** sind.  
  
6.  Wiederholen Sie die Schritte 1 bis 4, um eine Anmeldung für das lokale Konto repl_distribution zu erstellen. Diese Anmeldung muss einem Benutzer zugeordnet werden, der Mitglied der `db_owner` festgelegten Daten Bank Rolle in der **Verteilungs** Datenbank ist.  
  
7.  Wiederholen Sie die Schritte 1 bis 4, um eine Anmeldung für das lokale Konto repl_merge zu erstellen. Diese Anmeldung muss Benutzerzuordnungen in den Datenbanken **distribution** und **AdventureWorks** haben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verteilung konfigurieren](configure-distribution.md)   
 [Replikations-agentsicherheitsmodell](security/replication-agent-security-model.md)  
  
  
