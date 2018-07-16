---
title: Common Language Runtime (CLR) Integration Programmierkonzepte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- CLR [SQL Server] See common language runtime [SQL Server]
- Database Engine [SQL Server], .NET Framework
- .NET Framework [SQL Server], Database Engine programming
- common language runtime [SQL Server]
- .NET Framework [SQL Server]
ms.assetid: 951bf851-3e6e-4361-ae6a-2bcd5b837ebd
caps.latest.revision: 59
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: df157328c0718a55dae569503e1e5f6bd424131e
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37357032"
---
# <a name="common-language-runtime-clr-integration-programming-concepts"></a>Programmierkonzepte für die Common Language Runtime (CLR)-Integration
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] enthält [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Integration der CLR-Komponente (Common Language Runtime) des .NET Framework für [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Dies bedeutet, dass Sie gespeicherte Prozeduren, Trigger, benutzerdefinierte Typen, benutzerdefinierte Funktionen, benutzerdefinierte Aggregate und streaming Table-valued Function, jetzt schreiben können mit einer beliebigen .NET Framework-Sprache, einschließlich [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET und [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual c#.  
  
 Der Microsoft.SqlServer.Server-Namespace beinhaltet Kernfunktionalität für CLR-Programmierung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Der Microsoft.SqlServer.Server-Namespace hingegen ist im NET Framework SDK dokumentiert. Diese Dokumentation ist nicht in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Onlinedokumentation enthalten.  
  
> [!IMPORTANT]  
>  Standardmäßig ist .NET Framework unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert; dies gilt jedoch nicht für .NET Framework SDK. Wenn SDK auf Ihrem Computer nicht installiert ist und nicht in der Onlinedokumentation aufgeführt wird, funktionieren die in diesem Abschnitt aufgeführten Links zu SDK-Inhalten nicht. Installieren Sie das .NET Framework SDK. Fügen Sie das SDK nach der Installation der Onlinedokumentation und dem Inhaltsverzeichnis hinzu, indem Sie die Anweisungen unter [Installieren des .NET Framework SDKs](http://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)befolgen.  
  
> [!NOTE]  
>  CLR-Funktionalität, z. B. CLR User-Funktionen sind *nicht* für Azure SQL-Datenbank unterstützt.  
  
 In der folgenden Tabelle sind die Themen dieses Abschnitts aufgeführt.  
  
 [Common Language Runtime &#40;CLR&#41; Integration (Übersicht)](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md)  
 Enthält eine kurze Übersicht über die CLR und beschreibt, wie und warum diese Technologie verwendet wurde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Beschreibt die Vorteile der Verwendung von CLR zur Erstellung von Datenbankobjekten.  
  
 
  [Assemblys &amp;#40;Datenbank-Engine&amp;#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)  
 Beschreibt, wie Assemblys in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden, um Funktionen, gespeicherte Prozeduren, Trigger, benutzerdefinierte Aggregate und benutzerdefinierte Typen bereitzustellen, die in einer der verwalteten Codesprachen geschrieben wurden, die von der [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-CLR (Common Language Runtime) gehostet werden, und nicht in [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 [Erstellen von Datenbankobjekten mit Common Language Runtime &#40;CLR&#41; Integration](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md)  
 Beschreibt, welche Objekte mit CLR erstellt werden können, sowie die Anforderungen zur Erstellung von CLR-Datenbankobjekten.  
  
 [Datenzugriff von CLR-Datenbankobjekten aus](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
 Beschreibt, wie eine CLR-Routine auf Daten zugreifen kann, die in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeichert sind.  
  
 [Sicherheit der CLR-Integration](../../relational-databases/clr-integration/security/clr-integration-security.md)  
 Beschreibt das Sicherheitsmodell der CLR-Integration.  
  
 [Debuggen von CLR-Datenbankobjekten](../../relational-databases/clr-integration/debugging-clr-database-objects.md)  
 Beschreibt Einschränkungen und Anforderungen des Debuggens von CLR-Datenbankobjekten.  
  
 [Bereitstellen von CLR-Datenbankobjekten](../../relational-databases/clr-integration/deploying-clr-database-objects.md)  
 Beschreibt die Bereitstellung von Assemblys auf Produktionsservern.  
  
 [Verwalten von CLR-Integrationsassemblys](../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)  
 Beschreibt das Erstellen und Löschen der Assemblys zur CLR-Integration.  
  
 [Überwachung und Problembehandlung von verwalteten Datenbankobjekten](../../relational-databases/clr-integration/monitoring-and-troubleshooting-managed-database-objects.md)  
 Enthält Informationen zu den Tools, die verwendet werden können, Überwachung und Problembehandlung von verwalteten Datenbankobjekten und Assemblys in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Verwendungsszenarios und Beispiele für Common Language Runtime-Integration &#40;CLR&#41;](http://msdn.microsoft.com/library/33aac25f-abb4-4f29-af88-4a0dacd80ae7)  
 Beschreibt Verwendungsszenarien und Codebeispiele mit CLR-Objekten.  
  
## <a name="see-also"></a>Siehe auch  
 [Assemblys &#40;Datenbank-Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)   
 [Installieren von .NET Framework SDK](http://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)  
  
  
