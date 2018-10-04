---
title: 'Lektion 1: Erstellen von Windows-Konten für die Replikation | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
- replication [SQL Server], administering
ms.assetid: 65c3816b-47f0-448c-a4a4-ebd3e2a58820
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 0269a82d4ef11e53c41d7b288797064e0f3abd16
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095570"
---
# <a name="lesson-1-creating-windows-accounts-for-replication"></a>Lektion 1: Erstellen von Windows-Konten für die Replikation
  In dieser Lektion erstellen Sie Windows-Konten zum Ausführen von Replikations-Agents. Sie erstellen für die folgenden Agents ein separates Windows-Konto auf dem lokalen Server:  
  
|Agent|Speicherort|Kontoname|  
|-----------|--------------|------------------|  
|Momentaufnahme-Agent|Verleger|\<*machine_name*>\repl_snapshot|  
|Protokolllese-Agent|Verleger|\<*machine_name*>\repl_logreader|  
|Verteilungs-Agent|Verleger und Abonnent|\<*machine_name*>\repl_distribution|  
|Merge-Agent|Verleger und Abonnent|\<*machine_name*>\repl_merge|  
  
> [!NOTE]  
>  In den Replikationslernprogrammen wird für Verleger und Verteiler dieselbe Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gemeinsam verwendet. Verleger und Abonnent können dieselbe Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gemeinsam verwenden; dies ist jedoch keine Anforderung. Wenn der Verleger und Abonnent dieselbe Instanz verwenden, sind die Schritte zum Erstellen von Konten auf dem Verleger nicht erforderlich.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-publisher"></a>So erstellen Sie lokale Windows-Konten für Replikations-Agents auf dem Verleger  
  
1.  Öffnen Sie auf dem Verleger in der Systemsteuerung in **Verwaltung** das Tool **Computerverwaltung** .  
  
2.  Erweitern Sie unter **System**den Eintrag **Lokale Benutzer und Gruppen**.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Benutzer** und anschließend auf **Neuer Benutzer**.  
  
4.  Geben Sie `repl_snapshot` in die **Benutzernamen** , geben Sie das Kennwort und weitere relevante Informationen ein, und klicken Sie dann auf **erstellen** um das Konto Repl_snapshot zu erstellen.  
  
5.  Wiederholen Sie den letzten Schritt, um die Konten repl_logreader, repl_distribution und repl_merge zu erstellen.  
  
6.  Klicken Sie auf **Schließen**.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a>So erstellen Sie lokale Windows-Konten für Replikations-Agents auf dem Abonnenten  
  
1.  Öffnen Sie auf dem Abonnenten in der Systemsteuerung in **Verwaltung** das Tool **Computerverwaltung** .  
  
2.  Erweitern Sie unter **System**den Eintrag **Lokale Benutzer und Gruppen**.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Benutzer** und anschließend auf **Neuer Benutzer**.  
  
4.  Geben Sie `repl_distribution` in die **Benutzernamen** , geben Sie das Kennwort und weitere relevante Informationen ein, und klicken Sie dann auf **erstellen** das Konto repl_distribution zu erstellen.  
  
5.  Wiederholen Sie den letzten Schritt, um das Konto repl_merge zu erstellen.  
  
6.  Klicken Sie auf **Schließen**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie haben Windows-Konten für Replikations-Agents erfolgreich erstellt. Als Nächstes konfigurieren Sie den Momentaufnahmeordner. Weitere Informationen finden Sie unter [Lektion 2: Vorbereiten des Momentaufnahmeordners](lesson-2-preparing-the-snapshot-folder.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Replikations-Agents](agents/replication-agents-overview.md)  
  
  
