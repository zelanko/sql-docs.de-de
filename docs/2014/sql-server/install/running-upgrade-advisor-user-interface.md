---
title: Ausführen des Upgrade Advisors (Benutzeroberfläche) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Report Viewer
- Upgrade Advisor [SQL Server], running
- launching Upgrade Advisor
- Upgrade Advisor Analysis Wizard
- starting Upgrade Advisor
- SQL Server Upgrade Advisor, running
ms.assetid: 7f47c9b3-88d3-43d6-837e-f157b49a55ac
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5aecaea9bef359ad24aebbd20dd5e9547497043b
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66092446"
---
# <a name="running-upgrade-advisor-user-interface"></a>Ausführen des Upgrade Advisors (Benutzeroberfläche)
  Sie können den Upgrade Advisor ausführen, um lokale oder Remotekomponenten während der Upgradeplanung zu analysieren. Der Upgrade Advisor erzeugt einen Bericht für jede Komponente und die Instanz, die analysiert wird.  
  
> [!IMPORTANT]  
>  Der Upgrade Advisor analysiert keine Remoteinstanzen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Um eine Instanz von [!INCLUDE[ssRS](../../includes/ssrs.md)] zu analysieren, muss der Upgrade Advisor auf dem Computer installiert sein, auf dem [!INCLUDE[ssRS](../../includes/ssrs.md)] installiert ist.  
>   
>  Zum Analysieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services, muss Ihnen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] installiert und [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] auf demselben Computer installiert.  
  
## <a name="running-the-upgrade-advisor-analysis-wizard"></a>Ausführen des Analyse-Assistenten des Upgrade Advisors  
 Das Ausführen des Analyse-Assistenten des Upgrade Advisors erfolgt in sechs Schritten:  
  
1.  Starten Sie den Assistenten von der Startseite des Upgrade Advisors.  
  
2.  Identifizieren Sie die Server und Komponenten, die analysiert werden sollen.  
  
3.  Erfassen Sie Authentifizierungsinformationen.  
  
4.  Sammeln Sie zusätzliche Parameter auf der Grundlage des Komponententyps.  
  
5.  Analysieren Sie ausgewählte Komponenten.  
  
6.  Generieren Sie einen Bericht der Upgradeprobleme.  
  
 Weitere Informationen zu den Upgrade Advisor-Analyse-Assistenten, finden Sie unter [Vorgehensweise: Führen Sie den Analyse-Assistenten des Upgrade Advisors](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md).  
  
 Spezielle Informationen, die für jeden Schritt erforderlich ist, finden Sie unter [Upgrade Advisor-Benutzeroberflächenreferenz](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).  
  
## <a name="running-the-upgrade-advisor-report-viewer"></a>Der Berichts-Viewer von Upgrade Advisor ausführen  
 Sie verwenden den Upgrade Advisor-Berichts-Viewer zum Anzeigen von Berichten, die von der Analyse-Assistenten generiert. Wenn der Bericht geladen wird, können Sie die Komponenten des Berichts nach den folgenden Kriterien filtern:  
  
-   Alle Probleme  
  
-   Alle Ugradeprobleme  
  
-   Probleme vor dem Upgrade  
  
-   Alle Migrationsprobleme  
  
-   Behobene Probleme  
  
-   Ungelöste Probleme  
  
 Schrittweise Anweisungen zur Verwendung des Berichts-Viewers finden Sie in den folgenden Themen:  
  
-   [Vorgehensweise: Zeigen Sie einen der Upgrade Advisor-Bericht](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)  
  
-   [Vorgehensweise: Filterberichte](../../../2014/sql-server/install/how-to-filter-reports.md)  
  
-   [Vorgehensweise: Exportieren von Berichten](../../../2014/sql-server/install/how-to-export-reports.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Führen Sie den Analyse-Assistenten des Upgrade Advisors](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [Upgrade Advisor Referenz zur Benutzeroberfläche](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)   
 [Beheben von Upgradeproblemen](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
