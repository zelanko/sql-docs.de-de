---
title: Ändern des Controllers und der Clientdienstkonten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 44a73ddb-18ad-415c-bfbe-126ab2e3290b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6dbd6a425222c0e3f31d55a590294e9d3554f96e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48181110"
---
# <a name="modify-the-controller-and-client-services-accounts"></a>Ändern von Controller- und Clientdienstkonten
  In diesem Thema werden Änderungen der Distributed Replay Controller- und Clientdienstkonten und die erneute Anwendung der Zugriffssteuerungslisten (Access Control List, ACL) behandelt.  
  
### <a name="to-start-or-stop-the-distributed-replay-services-using-computer-management"></a>So starten oder beenden Sie die Distributed Replay-Dienste über die Computerverwaltung  
  
1.  Geben Sie auf dem Computer, auf dem der Distributed Replay-Diensten, an der Eingabeaufforderung den Befehl installiert sind `dcomcnfg`.  
  
2.  Doppelklicken Sie auf **Dienste**, scrollen Sie nach unten, und klicken Sie mit der rechten Maustaste auf **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay \<Dienstname>**. Klicken Sie anschließend auf **Start** oder auf **Beenden**.  
  
### <a name="to-modify-the-distributed-replay-controller-service"></a>So ändern Sie den Distributed Replay Controller-Dienst  
  
1.  Beenden Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller-Dienst auf dem Controllercomputer.  
  
2.  Klicken Sie unter **Dienste**mit der rechten Maustaste auf **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller**, und wählen Sie dann **Eigenschaften**aus.  
  
3.  Wählen Sie im Fenster **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller** auf der Registerkarte **Anmelden** die Option **Dieses Konto**aus, geben Sie das neue Anmeldekonto ein, oder klicken Sie auf **Durchsuchen** , um dieses zu suchen. Klicken Sie dann auf **OK**.  
  
     **Wichtig**: Wenn Sie den Distributed Replay Controller konfigurieren, können Sie mindestens ein Benutzerkonto angeben, das zum Ausführen der Distributed Replay Client-Dienste verwendet wird. Die folgenden Kontotypen werden unterstützt:  
  
    -   Domänenbenutzerkonto  
  
    -   Vom Benutzer erstelltes lokales Benutzerkonto  
  
    -   Administrator  
  
    -   Virtuelles Konto und verwaltetes Dienstkonto (Managed Service Account, MSA)  
  
    -   Netzwerkdienste, lokale Dienste und System  
  
     Gruppenkonten (lokales oder Domänenbenutzerkonto) und andere integrierte Konten (wie "Jeder") werden nicht akzeptiert.  
  
4.  Starten Sie den Distributed Replay Controller-Dienst.  
  
### <a name="to-modify-the-distributed-replay-client-service"></a>So ändern Sie den Distributed Replay Client-Dienst  
  
1.  Bevor Sie den Distributed Replay Client-Dienst ändern, sollten Sie sicherstellen, dass das zu ändernde Clientdienstkonto (auf dem Controllercomputer im CTLRUSERS-Parameter) während des Setupvorgangs angegeben wurde. Wenn das Clientdienstkonto, das Sie ändern, während des Setups nicht angegeben wurde, müssen Sie zuerst die folgenden Schritte ausführen:  
  
    1.  Beenden Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay-Controllerdienst.  
  
    2.  Geben Sie auf dem Controllercomputer, auf dem der Controllerdienst, über die Eingabeaufforderung installiert ist `dcomcnfg`.  
  
    3.  Navigieren Sie im Fenster **Komponentendienste** zu **Konsolenstamm > Komponentendienste > Computer > Arbeitsplatz > DCOM Config > DReplayController**.  
  
    4.  Klicken Sie mit der rechten Maustaste auf **DReplayController**, und klicken Sie anschließend auf **Eigenschaften**.  
  
    5.  Klicken Sie im Fenster **Eigenschaften von DReplayController** auf der Registerkarte **Sicherheit** im Abschnitt **Start- und Aktivierungsberechtigungen** auf **Bearbeiten** .  
  
    6.  Erteilen Sie die dem neuen Clientdienst-Anmeldekonto die Berechtigungen **Lokale Aktivierung** und Remoteaktivierung, und klicken Sie dann auf **OK**.  
  
    7.  Klicken Sie im Abschnitt **Zugriffsberechtigungen** auf **Bearbeiten** , gewähren Sie dem neuen Clientdienst-Anmeldekonto die Berechtigungen **Lokaler Zugriff** und Remotezugriff, und klicken Sie dann auf **OK**.  
  
    8.  Klicken Sie auf **OK** , um das Fenster **Eigenschaften von DReplayController** zu schließen.  
  
    9. Fügen Sie auf dem Controllercomputer der Gruppe **Distributed COM-Benutzer** das geänderte Clientdienst-Anmeldekonto hinzu.  
  
    10. Starten Sie den SQL Server Distributed Replay Controller-Dienst.  
  
2.  Beenden Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client-Dienst.  
  
3.  Wählen Sie im Fenster **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client** auf der Registerkarte **Anmelden** die Option **Dieses Konto**aus, geben Sie das neue Anmeldekonto ein, oder klicken Sie auf **Durchsuchen** , um dieses zu suchen. Klicken Sie dann auf **OK**.  
  
4.  Starten Sie den Distributed Replay Client-Dienst.  
  
  
