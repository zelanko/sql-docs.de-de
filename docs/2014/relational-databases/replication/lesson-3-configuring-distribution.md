---
title: 'Lektion 3: Konfigurieren der Verteilung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f248984a-0b59-4c2f-a56d-31f8dafe72b5
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ab6c3ab7b14b8e7443b9ac6b39225aa02671fa88
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057833"
---
# <a name="lesson-3-configuring-distribution"></a>Lektion 3: Konfigurieren der Verteilung
  In dieser Lektion konfigurieren Sie die Verteilung auf dem Verleger und legen die erforderlichen Berechtigungen für die Verteilungs- und Veröffentlichungsdatenbanken fest. Wenn der Verteiler bereits konfiguriert wurde, müssen die Veröffentlichung und die Verteilung erst deaktiviert werden, bevor Sie mit dieser Lektion beginnen. Führen Sie diese Lektion nicht aus, wenn Sie eine vorhandene Replikationstopologie beibehalten müssen.  
  
 Das Konfigurieren eines Verlegers mit einem Remoteverteiler wird in diesem Lernprogramm nicht behandelt.  
  
### <a name="configuring-distribution-at-the-publisher"></a>Konfigurieren der Verteilung auf dem Verleger  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Ordner **Replikation**, und klicken Sie anschließend auf **Verteilung konfigurieren**.  
  
    > [!NOTE]  
    >  Wenn Sie **localhost[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anstelle des tatsächlichen Servernamens verwendet haben, um eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herzustellen, werden Sie in einer Warnmeldung darauf hingewiesen, dass**  nicht in der Lage ist, eine Verbindung mit dem Server **"localhost"** herzustellen. Klicken Sie im Warnungsdialogfeld auf **OK**. Ändern Sie im Dialogfeld **Verbindung mit Server herstellen** die Angabe für **Servername** von **localhost** in den Namen des Servers. Klicken Sie auf **Verbinden**.  
  
     Der Verteilungskonfigurations-Assistent wird gestartet.  
  
3.  Auf der **Verteiler** Seite **"***\<ServerName >***" fungiert als sein eigener Verteiler; SQL Server erstellt eine Verteilungsdatenbank und ein Protokoll**, und klicken Sie dann auf **Weiter**.  
  
4.  Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht ausgeführt wird, wählen Sie auf der Seite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**Agent-Start** die Option **Ja**, den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zum automatischen Starten konfigurieren. Klicken Sie auf **Weiter**.  
  
5.  Geben Sie im Textfeld **Momentaufnahmeordner** die Zeichenfolge **\\\\**\<*Computername>***\repldata** ein, wobei \<*Computername>* der Name des Verlegers ist, und klicken Sie anschließend auf **Weiter**.  
  
6.  Übernehmen Sie die Standardwerte auf den restlichen Seiten des Assistenten.  
  
7.  Klicken Sie auf **Fertig stellen** , um die Verteilung zu aktivieren.  
  
### <a name="setting-database-permissions-at-the-publisher"></a>Festlegen der Datenbankberechtigungen auf dem Verleger  
  
1.  Erweitern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]den Knoten **Sicherheit**, klicken Sie mit der rechten Maustaste auf **Anmeldungen**, und wählen Sie anschließend **Neue Anmeldung**aus.  
  
2.  Klicken Sie auf der Seite **Allgemein** auf **Suchen**, geben Sie im Feld **Geben Sie die zu verwendenden Objektnamen** die Zeichenfolge \<*Computername>***\repl_snapshot** ein, wobei \<*Computername>* der Name des lokalen Verlegerservers ist. Klicken Sie auf **Namen überprüfen**, und klicken Sie anschließend auf **OK**.  
  
3.  Wählen Sie auf der Seite **Benutzerzuordnung** in der Liste **Benutzer, die dieser Anmeldung zugeordnet sind** sowohl die **Verteilungs** - als auch die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank aus.  
  
     In der **Mitgliedschaft in Datenbankrolle** Liste Wählen Sie die `db_owner` Rolle für die Anmeldung für beide Datenbanken.  
  
4.  Klicken Sie auf **OK** , um die Anmeldung zu erstellen.  
  
5.  Wiederholen Sie die Schritte 1 bis 4, um eine Anmeldung für das lokale Konto repl_logreader zu erstellen. Diese Anmeldung muss auch für Benutzer, die Elemente zugeordnet werden die `db_owner` festen Datenbankrolle "" in der **Verteilung** und **AdventureWorks** Datenbanken.  
  
6.  Wiederholen Sie die Schritte 1 bis 4, um eine Anmeldung für das lokale Konto repl_distribution zu erstellen. Diese Anmeldung muss ein Benutzer, der ein Mitglied ist zugeordnet werden die `db_owner` festen Datenbankrolle "" in der **Verteilung** Datenbank.  
  
7.  Wiederholen Sie die Schritte 1 bis 4, um eine Anmeldung für das lokale Konto repl_merge zu erstellen. Diese Anmeldung muss Benutzerzuordnungen in den Datenbanken **distribution** und **AdventureWorks** haben.  
  
## <a name="see-also"></a>Siehe auch  
 [Verteilung konfigurieren](configure-distribution.md)   
 [Replication Agent Security Model](security/replication-agent-security-model.md)  
  
  