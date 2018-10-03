---
title: Auswählen des richtigen SQL Server-Agent-Dienst-Dienstkontos für Multiserverumgebungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- multiserver environments [SQL Server], SQL Server Agent service account behavior
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ed13a65b6cecee8d45235368f3b6f8f120f64ede
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069240"
---
# <a name="choose-the-right-sql-server-agent-service-account-for-multiserver-environments"></a>Auswählen des richtigen SQL Server-Agent-Dienstkontos für Multiserverumgebungen
  Das Windows-Konto, das Sie für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst auswählen, kann sich wie im Folgenden beschrieben auf das Verhalten einer Multiserverumgebung auswirken:  
  
-   Wenn Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst unter einem Konto ausführen, das nicht Mitglied der lokalen Windows-Administratorengruppe ist, treten beim Eintragen von Zielservern bei Masterservern u. U. Fehler auf. In diesem Fall wird die folgende Fehlermeldung zurückgegeben:  
  
     "Fehler beim Eintragungsvorgang."  
  
     Starten Sie die Dienste von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent neu, um das Problem zu beheben.  
  
-   Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst unter dem Konto LocalSystem ausgeführt wird, werden Vorgänge zwischen Masterservern und Zielservern nur unterstützt, wenn sich Masterserver und Zielserver auf demselben Computer befinden. Wenn Sie diese Konfiguration verwenden, wird beim Eintragen von Zielservern bei einem Masterserver die folgende Meldung zurückgegeben:  
  
     „Stellen Sie sicher, dass das Agentstartkonto für *<Zielserver-Computername>* Rechte zur Anmeldung als Zielserver besitzt.“  
  
     Sie können diese zu Informationszwecken ausgegebene Meldung ignorieren. Der Eintragungsvorgang wird dennoch erfolgreich abgeschlossen.  
  
 Weitere Informationen zum Auswählen eines Kontos für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst finden Sie unter [Auswählen eines Kontos für den SQL Server-Agent-Dienst](select-an-account-for-the-sql-server-agent-service.md).  
  
  
