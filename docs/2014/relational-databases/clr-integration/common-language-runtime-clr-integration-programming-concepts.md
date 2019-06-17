---
title: Common Language Runtime (CLR) Integration Programmierkonzepte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- CLR [SQL Server] See common language runtime [SQL Server]
- Database Engine [SQL Server], .NET Framework
- .NET Framework [SQL Server], Database Engine programming
- common language runtime [SQL Server]
- .NET Framework [SQL Server]
ms.assetid: 951bf851-3e6e-4361-ae6a-2bcd5b837ebd
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: ffd706cdb17bd73281ee4a62842362b09c6311ef
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62922554"
---
# <a name="common-language-runtime-clr-integration-programming-concepts"></a>Programmierkonzepte für die Common Language Runtime (CLR)-Integration
  Ab [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]enthält [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die Integration der CLR-Komponente (Common Language Runtime) des .NET Framework für [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Das bedeutet, dass Sie jetzt gespeicherte Prozeduren, Trigger, benutzerdefinierte Typen, benutzerdefinierte Funktionen, benutzerdefinierte Aggregate und Streaming-Tabellenwertfunktionen mit einer beliebigen .NET Framework-Sprache schreiben können, einschließlich [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET und [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.  
  
 Der Microsoft.SqlServer.Server-Namespace beinhaltet Kernfunktionalität für die CLR-Programmierung in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Der Microsoft.SqlServer.Server-Namespace hingegen ist im NET Framework SDK dokumentiert. Diese Dokumentation ist nicht in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] der Onlinedokumentation enthalten.  
  
> [!IMPORTANT]  
>  Standardmäßig ist .NET Framework unter [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]installiert; dies gilt jedoch nicht für .NET Framework SDK. Wenn SDK auf Ihrem Computer nicht installiert ist und nicht in der Onlinedokumentation aufgeführt wird, funktionieren die in diesem Abschnitt aufgeführten Links zu SDK-Inhalten nicht. Installieren Sie das .NET Framework SDK. Fügen Sie das SDK nach der Installation der Onlinedokumentation und dem Inhaltsverzeichnis hinzu, indem Sie die Anweisungen unter [Installieren des .NET Framework SDKs](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)befolgen.  
  
 In der folgenden Tabelle sind die Themen dieses Abschnitts aufgeführt.  
  
 [Common Language Runtime &#40;CLR&#41; Integration (Übersicht)](common-language-runtime-integration-overview.md)  
 Bietet eine kurze Übersicht über CLR und beschreibt die Verwendung dieser Technologie in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Beschreibt die Vorteile der Verwendung von CLR zur Erstellung von Datenbankobjekten.  
  
 [Assemblys &#40;Datenbank-Engine&#41;](assemblies-database-engine.md)  
 Beschreibt, wie Assemblys in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet werden, um Funktionen, gespeicherte Prozeduren, Trigger, benutzerdefinierte Aggregate und benutzerdefinierte Typen bereitzustellen, die in einer der verwalteten Codesprachen geschrieben wurden, die von der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework-CLR (Common Language Runtime) gehostet werden, und nicht in [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 [Erstellen von Datenbankobjekten mit Common Language Runtime &#40;CLR&#41; Integration](database-objects/building-database-objects-with-common-language-runtime-clr-integration.md)  
 Beschreibt, welche Objekte mit CLR erstellt werden können, sowie die Anforderungen zur Erstellung von CLR-Datenbankobjekten.  
  
 [Datenzugriff von CLR-Datenbankobjekten aus](data-access/data-access-from-clr-database-objects.md)  
 Beschreibt, wie eine CLR-Routine auf Daten zugreifen kann, die in einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]gespeichert sind.  
  
 [Sicherheit der CLR-Integration](security/clr-integration-security.md)  
 Beschreibt das Sicherheitsmodell der CLR-Integration.  
  
 [Debuggen von CLR-Datenbankobjekten](debugging-clr-database-objects.md)  
 Beschreibt Einschränkungen und Anforderungen des Debuggens von CLR-Datenbankobjekten.  
  
 [Bereitstellen von CLR-Datenbankobjekten](deploying-clr-database-objects.md)  
 Beschreibt die Bereitstellung von Assemblys auf Produktionsservern.  
  
 [Verwalten von CLR-Integrationsassemblys](assemblies/managing-clr-integration-assemblies.md)  
 Beschreibt das Erstellen und Löschen der Assemblys zur CLR-Integration.  
  
 [Überwachung und Problembehandlung von verwalteten Datenbankobjekten](monitoring-and-troubleshooting-managed-database-objects.md)  
 Enthält Informationen zu den Tools, die zum Überwachen und zur Problembehandlung von verwalteten Datenbankobjekten und Assemblys in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]verwendet werden können.  
  
 [Verwendungsszenarios und Beispiele für Common Language Runtime-Integration &#40;CLR&#41;](../../database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
 Beschreibt Verwendungsszenarien und Codebeispiele mit CLR-Objekten.  
  
## <a name="see-also"></a>Siehe auch  
 [Assemblys &#40;Datenbank-Engine&#41;](assemblies-database-engine.md)   
 [Installieren von .NET Framework SDK](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)  
  
  
