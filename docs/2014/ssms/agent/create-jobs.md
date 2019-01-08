---
title: Erstellen von Aufträgen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: 465fb7fc-7622-4252-a178-ea51691c935b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 986e38ef42fe1af2aba8ba1625225a336f29158d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52751312"
---
# <a name="create-jobs"></a>Erstellen von Aufträgen
  Ein Auftrag besteht aus einer festgelegten Folge von Operationen, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent der Reihenfolge nach ausführt. Über einen Auftrag können zahlreiche Aktivitäten ausgeführt werden, u. a. das Ausführen von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts, Eingabeaufforderungsanwendungen, Microsoft ActiveX-Skripts, Integration Services-Paketen, Analysis Services-Befehlen und -abfragen bzw. Replikationstasks. Aufträge können wiederholte oder planbare Tasks ausführen, und sie können Benutzer in Form von Warnungen hinsichtlich des Auftragsstatus benachrichtigen. Dies führt zu einer deutlichen Vereinfachung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verwaltung.  
  
 Um einen Auftrag erstellen zu können, muss ein Benutzer Mitglied einer der festen Datenbankrollen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents oder Mitglied der festen Serverrolle **sysadmin** sein. Ein Auftrag kann nur von seinem Besitzer bzw. Mitgliedern der **sysadmin** -Rolle bearbeitet werden. Mitglieder der **sysadmin** -Rolle können anderen Benutzern den Auftragsbesitz zuweisen und sämtliche Aufträge ausführen, ungeachtet des Auftragsbesitzers. Weitere Informationen zu den festen Datenbankrollen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](sql-server-agent-fixed-database-roles.md).  
  
 Aufträge können so geschrieben werden, dass sie auf der lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder auf mehreren Instanzen in einem Unternehmen ausgeführt werden. Zum Ausführen von Aufträgen auf mehreren Servern müssen Sie mindestens einen Masterserver und einen oder mehrere Zielserver einrichten. Weitere Informationen zu Master- und Zielservern finden Sie unter [Automatisierte Verwaltung in einem Unternehmen](automated-administration-across-an-enterprise.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent zeichnet die Informationen von Aufträgen und Auftragsschritten im Auftragsverlauf auf.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Beschreibung**|**Thema**|  
|Beschreibt, wie ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Auftrag erstellt wird.|[Erstellen eines Auftrags](create-a-job.md)|  
|Beschreibt, wie Sie den Besitz eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Auftrags einem anderen Benutzer neu zuweisen können.|[Give Others Ownership of a Job](give-others-ownership-of-a-job.md)|  
|Beschreibt, wie Sie das Auftragsverlaufsprotokoll des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents einrichten.|[Set Up the Job History Log](set-up-the-job-history-log.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Auftragsschritten](manage-job-steps.md)   
 [Automatisierte Verwaltung in einem Unternehmen](automated-administration-across-an-enterprise.md)   
 [Erstellen und Zuweisen von Zeitplänen zu Aufträgen](create-and-attach-schedules-to-jobs.md)   
 [Ausführen von Aufträgen](run-jobs.md)   
 [Anzeigen oder Ändern von Aufträgen](view-or-modify-jobs.md)  
  
  
