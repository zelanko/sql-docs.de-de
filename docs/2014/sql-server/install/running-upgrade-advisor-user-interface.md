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
ms.openlocfilehash: 653e3d0565d0b32c67ccf77772a9b89f611dd082
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058946"
---
# <a name="running-upgrade-advisor-user-interface"></a>Ausführen des Upgrade Advisors (Benutzeroberfläche)
  Sie können den Upgrade Advisor ausführen, um lokale oder Remotekomponenten während der Upgradeplanung zu analysieren. Der Upgrade Advisor erzeugt einen Bericht für jede Komponente und Instanz, die analysiert wird.  
  
> [!IMPORTANT]  
>  Der Upgrade Advisor analysiert keine Remoteinstanzen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Um eine Instanz von [!INCLUDE[ssRS](../../includes/ssrs.md)] zu analysieren, muss der Upgrade Advisor auf dem Computer installiert sein, auf dem [!INCLUDE[ssRS](../../includes/ssrs.md)] installiert ist.  
>   
>  Um Integration Services zu analysieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , muss [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] installiert und [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] auf dem gleichen Computer installiert sein.  
  
## <a name="running-the-upgrade-advisor-analysis-wizard"></a>Ausführen des Analyse-Assistenten des Upgrade Advisors  
 Das Ausführen des Analyse-Assistenten des Upgrade Advisors erfolgt in sechs Schritten:  
  
1.  Starten Sie den Assistenten von der Startseite des Upgrade Advisors.  
  
2.  Identifizieren Sie die Server und Komponenten, die analysiert werden sollen.  
  
3.  Erfassen Sie Authentifizierungsinformationen.  
  
4.  Sammeln Sie zusätzliche Parameter auf der Grundlage des Komponententyps.  
  
5.  Analysieren Sie ausgewählte Komponenten.  
  
6.  Generieren Sie einen Bericht der Upgradeprobleme.  
  
 Weitere Informationen zum Analyse-Assistenten des Upgrade Advisors finden Sie unter Gewusst [wie: Ausführen des Analyse-Assistenten für den Upgrade Advisor](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md).  
  
 Spezifische Informationen, die für die einzelnen Schritte erforderlich sind, finden Sie unter [Referenz zur Benutzeroberfläche des Upgrade Advisors](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).  
  
## <a name="running-the-upgrade-advisor-report-viewer"></a>Ausführen des Berichts-Viewers des Upgrade Advisors  
 Mit dem Berichts-Viewer des Upgrade Advisors können Sie Berichte anzeigen, die vom Analyse-Assistenten des Upgrade Advisors generiert wurden. Wenn der Bericht geladen wird, können Sie die Komponenten des Berichts nach den folgenden Kriterien filtern:  
  
-   Alle Probleme  
  
-   Alle Ugradeprobleme  
  
-   Probleme vor dem Upgrade  
  
-   Alle Migrationsprobleme  
  
-   Behobene Probleme  
  
-   Ungelöste Probleme  
  
 Schrittweise Anweisungen zur Verwendung des Berichts-Viewers finden Sie in den folgenden Themen:  
  
-   [Gewusst wie: Anzeigen eines Berichts des Upgrade Advisors](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)  
  
-   [Gewusst wie: Filtern von Berichten](../../../2014/sql-server/install/how-to-filter-reports.md)  
  
-   [Gewusst wie: Exportieren von Berichten](../../../2014/sql-server/install/how-to-export-reports.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorgehensweise: Ausführen des Analyse-Assistenten des Upgrade Advisors](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [Referenz zur Benutzeroberfläche des Upgrade Advisors](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)   
 [Beheben von Upgradeproblemen](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
