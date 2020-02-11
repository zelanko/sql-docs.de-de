---
title: Implementieren von Aufträgen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent]
- SQL Server Agent jobs
- SQL Server Agent jobs, about jobs
- jobs [SQL Server Agent], about jobs
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cef657960da876b25003a6fc1017a372abe410a0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63074015"
---
# <a name="implement-jobs"></a>Implementieren von Aufträgen
  Sie können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Aufträge verwenden, um regelmäßig anfallende administrative Tasks zu automatisieren und periodisch ausführen, sodass die Effizienz der Verwaltung verbessert wird.  
  
 Ein Auftrag besteht aus einer festgelegten Folge von Operationen, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent der Reihenfolge nach ausführt. Ein Auftrag kann eine Reihe von Aktivitäten ausführen, z. B. das Ausführen von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts, Befehlszeilenanwendungen, Microsoft ActiveX-Skripts, Integration Services-Paketen, Analysis Services-Befehlen und -Abfragen sowie Replikationstasks. Aufträge können wiederkehrende oder planbare Tasks ausführen, und sie können Benutzer durch Generieren von Warnungen automatisch über den Auftragsstatus informieren, sodass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verwaltung erheblich vereinfacht wird.  
  
 Sie können einen Auftrag manuell ausführen oder ihn so konfigurieren, dass er gemäß einem Zeitplan oder als Reaktion auf Warnungen ausgeführt wird.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Beschreibung**|**Thema**|  
|Enthält Informationen zum Erstellen von Aufträgen und Zuweisen des Besitz.|[Erstellen von Aufträgen](create-jobs.md)|  
|Enthält Informationen zum Organisieren von Aufträgen in Kategorien.|[Aufträge organisieren](organize-jobs.md)|  
|Enthält Informationen zu den verschiedenen Auftragsschritten, die Sie erstellen können, und beschreibt, wie Sie diese Auftragsschritte verwalten.|[Verwalten von Auftragsschritten](manage-job-steps.md)|  
|Enthält Informationen zur Definition des Auftragsbeginns sowie der Häufigkeit der Ausführung.|[Anlegen und Zuweisen von Zeitplänen zu Aufträgen](create-and-attach-schedules-to-jobs.md)|  
|Enthält Informationen zur manuellen Ausführung von Aufträgen (ohne Zeitplan).|[Ausführen von Aufträgen](run-jobs.md)|  
|Enthält Informationen zur Konfiguration des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents für die Reaktion auf Aufträge. Sie können den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent z. B. so konfigurieren, dass Administratoren bei der Beendigung von Aufträgen benachrichtigt werden.|[Angeben von Auftragsantworten](specify-job-responses.md)|  
|Enthält Informationen zum Anzeigen vorhandener Aufträge, zum Auftragsverlauf nach der Ausführung und zum Ändern von Aufträgen.|[Anzeigen oder Ändern von Aufträgen](view-or-modify-jobs.md)|  
|Enthält Informationen zum Löschen von Aufträgen.|[Löschen von Aufträgen](delete-jobs.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md)  
  
  
