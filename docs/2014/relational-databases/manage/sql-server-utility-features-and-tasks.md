---
title: Funktionen und Tasks im SQL Server-Hilfsprogramm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server utility [SQL Server]
- utility control point
- Utility growth rate
- Multiserver management
- UCP
- Multi-server management [SQL Server]
ms.assetid: 6e6cbd25-6b1c-4e21-9ade-4584e243fd8f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 81d816d58780f32eeaca64c1d90257eef1a8aaff
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48056703"
---
# <a name="sql-server-utility-features-and-tasks"></a>Funktionen und Tasks im SQL Server-Hilfsprogramm
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Kunden möchten ihre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Umgebung als Ganzes verwalten. Diese Anforderung wird in dieser Version mithilfe des Konzepts der Anwendungs- und Multiserververwaltung im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm erfüllt.  
  
## <a name="benefits-of-the-sql-server-utility"></a>Vorteile des SQL Server-Hilfsprogramms  
 Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm modelliert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-bezogene Entitäten eines Unternehmens in einer einheitlichen Ansicht. Die Blickpunkte des Hilfsprogramm-Explorers und des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramms in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) vermitteln Administratoren über eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die als Steuerungspunkt für das Hilfsprogramm (UCP) dient, eine ganzheitliche Sicht auf die Ressourcenintegrität in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Die Kombination aus Zusammenfassungsdaten und detaillierten Daten, die im UCP für Richtlinien sowohl für die Unter- als auch für die Überauslastung und für eine Vielzahl von Schlüsselparametern angezeigt werden, eröffnen neue Möglichkeiten der Ressourcenkonsolidierung und erleichtern die Erkennung von Ressourcen, die überausgelastet sind. Integritätsrichtlinien sind konfigurierbar und können angepasst werden, indem der obere oder untere Grenzwert für die Ressourcennutzung geändert wird. Sie können globale Überwachungsrichtlinien ändern oder einzelne Überwachungsrichtlinien für jede Entität konfigurieren, die im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm verwaltet wird.  
  
##  <a name="typical_scenarios"></a> Erste Schritte mit dem SQL Server-Hilfsprogramm  
 Am Anfang eines typischen Benutzerszenarios steht die Erstellung eines Steuerungspunkts für das Hilfsprogramm, der den zentralen Ansatzpunkt für das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm darstellt. Der UCP stellt eine konsolidierte Sicht der Ressourcenintegrität bereit, die von verwalteten Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm gesammelt wurde. Registrieren Sie nach der Erstellung des UCP Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm, damit sie vom UCP verwaltet werden können.  
  
 Jede [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz und Datenebenenanwendung, die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm verwaltet wird, kann auf der Grundlage globaler oder individueller Richtliniendefinitionen überwacht werden.  
  
## <a name="related-tasks"></a>Related Tasks  
 Erste Schritte mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm mithilfe der folgenden Themen:  
  
|||  
|-|-|  
|**Beschreibung**|**Thema**|  
|Beschreibt Überlegungen zum Konfigurieren eines Servers, um Sammlungssätze, die zum Hilfsprogramm und die nicht zum Hilfsprogramm gehören, auf der gleichen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]auszuführen.|[Überlegungen zum Ausführen von Hilfsprogramm- und Nicht-Hilfsprogramm-Sammlungssätzen auf derselben Instanz von SQL Server](run-utility-and-non-utility-collection-sets-on-same-sql-instance.md)|  
|Beschreibt, wie ein SQL Server-Steuerungspunkt für das Hilfsprogramm erstellt wird.|[Erstellen eines Steuerungspunkts für das SQL Server-Hilfsprogramm &#40;SQL Server-Hilfsprogramm&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md)|  
|Beschreibt, wie eine Verbindung mit einem SQL Server-Hilfsprogramm hergestellt wird.|[Verbinden mit einem SQL Server-Hilfsprogramm](connect-to-a-sql-server-utility.md)|  
|Beschreibt, wie eine Instanz von SQL Server mit einem Steuerungspunkt für das Hilfsprogramm registriert wird.|[Registrieren einer Instanz von SQL Server &#40;SQL Server-Hilfsprogramm&#41;](enroll-an-instance-of-sql-server-sql-server-utility.md)|  
|Beschreibt, wie der Hilfsprogramm-Explorer zum Verwalten des SQL Server-Hilfsprogramms verwendet wird.|[Verwenden des Hilfsprogramm-Explorers zum Verwalten des SQL Server-Hilfsprogramms](use-utility-explorer-to-manage-the-sql-server-utility.md)|  
|Beschreibt, wie Instanzen von SQL Server im SQL Server-Hilfsprogramm überwacht werden.|[Überwachen von SQL Server-Instanzen im SQL Server-Hilfsprogramm](monitor-instances-of-sql-server-in-the-sql-server-utility.md)|  
|Beschreibt, wie Ergebnisse zu Ressourcenintegritätsrichtlinien angezeigt werden.|[Anzeigen der Ergebnisse zu Ressourcenintegritätsrichtlinien &#40;SQL Server-Hilfsprogramm&#41;](view-resource-health-policy-results-sql-server-utility.md)|  
|Beschreibt, wie Definitionen von Ressourcenintegritätsrichtlinien geändert werden.|[Ändern der Definition von Ressourcenintegritätsrichtlinien &#40;SQL Server-Hilfsprogramm&#41;](modify-a-resource-health-policy-definition-sql-server-utility.md)|  
|Beschreibt, wie das UCP-Data Warehouse konfiguriert wird.|[Konfigurieren des Data Warehouse für den Steuerungspunkt für das Hilfsprogramm &#40;SQL Server-Hilfsprogramm&#41;](configure-your-utility-control-point-data-warehouse-sql-server-utility.md)|  
|Beschreibt, wie Integritätsrichtlinien für das Hilfsprogramm konfiguriert werden.|[Konfigurieren von Integritätsrichtlinien &#40;SQL Server-Hilfsprogramm&#41;](configure-health-policies-sql-server-utility.md)|  
|Beschreibt, wie die Abschwächung in CPU-Auslastungsrichtlinien angepasst wird.|[Reduzieren von Informationsrauschen bei Richtlinien zur CPU-Auslastung &#40;SQL Server-Hilfsprogramm&#41;](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)|  
|Beschreibt, wie eine Instanz von SQL Server aus einem UCP entfernt wird.|[Entfernen einer Instanz von SQL Server aus dem SQL Server-Hilfsprogramm](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)|  
|Beschreibt, wie das Proxykonto für den Hilfsprogramm-Datensammler auf einer verwalteten Instanz von SQL Server geändert wird.|[Ändern des Proxykontos für den Hilfsprogramm-Sammlungssatz auf einer verwalteten Instanz von SQL Server &#40;SQL Server-Hilfsprogramm&#41;](change-proxy-account-for-utility-collection-on-managed-sql-server.md)|  
|Beschreibt, wie UCPs von einer SQL Server-Instanz in eine andere verschoben werden.|[Verschieben eines UCPs von einer SQL Server-Instanz in eine andere &#40;SQL Server-Hilfsprogramm&#41;](move-a-ucp-from-one-instance-of-sql-server-to-another-sql-server-utility.md)|  
|Beschreibt, wie ein UCP entfernt wird.|[Entfernen eines Steuerungspunkts für das Hilfsprogramm &#40;SQL Server-Hilfsprogramm&#41;](remove-a-utility-control-point-sql-server-utility.md)|  
|Beschreibt, wie Fehler des SQL Server-Hilfsprogramms behoben werden.|[Problembehandlung beim SQL Server-Hilfsprogramm](../../database-engine/troubleshoot-the-sql-server-utility.md)|  
|Beschreibt, wie Fehler der SQL Server-Ressourcenintegrität behoben werden.|[Fehlerbehebung für die SQL Server-Ressourcenintegrität &#40;SQL Server-Hilfsprogramm&#41;](troubleshoot-sql-server-resource-health-sql-server-utility.md)|  
|Stellt Links zu UtilityExplorer-F1-Hilfethemen bereit.|[Hilfsprogramm-Explorer (F1-Hilfe)](utility-explorer-f1-help.md)|  
  
  
