---
title: Übersicht über die CLR-Integration (Common Language Runtime) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- managed code [SQL Server]
- common language runtime [SQL Server], about CLR integration
- cross-language integration
- integrating CLR [SQL Server]
- .NET Framework [SQL Server], common language runtime
- code access security [CLR integration]
- managed code [SQL Server], CLR integration
ms.assetid: 7be9e644-36a2-48fc-9206-faf59fdff4d7
author: rothja
ms.author: jroth
ms.openlocfilehash: 5d858dde63a43a0b929f3e091d0c0b295b268f5b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970680"
---
# <a name="common-language-runtime-clr-integration-overview"></a>Übersicht über die CLR-Integration (Common Language Runtime)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]bietet jetzt die Integration der Common Language Runtime (CLR)-Komponente des .NET Framework für [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Die CLR-Komponente stellt verwalteten Code mit Diensten bereit, wie z. B. sprachübergreifende Integration, Codezugriffssicherheit, Verwaltung der Objektlebensdauer und Debug- und Profilerstellungsunterstützung. Für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Benutzer und -Anwendungsentwickler bedeutet die CLR-Integration, dass sie nunmehr gespeicherte Prozeduren, Trigger, benutzerdefinierte Typen, benutzerdefinierte Funktionen (Skalar- und Tabellenwertfunktionen) sowie benutzerdefinierte Aggregatfunktionen mit einer beliebigen .NET Framework-Sprache, einschließlich [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET und [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#, schreiben können. In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ist .NET Framework, Version 4, vorinstalliert.  
  
 Zu den Hauptvorteilen dieser Integration zählen folgende:  
  
-   **Ein besseres Programmiermodell.** Die .NET Framework-Sprachen sind in vielerlei Hinsicht umfassender als Transact-SQL. Sie bieten Konstrukte und Fähigkeiten, die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Entwicklern zuvor nicht zur Verfügung standen. Entwickler können zudem die leistungsfähigen Funktionen der .NET Framework-Bibliothek nutzen, die einen umfassenden Satz Klassen bereitstellt. Diese ermöglichen es, Programmierungsprobleme schnell und effizient zu lösen.  
  
-   **Verbesserte Sicherheit und Zuverlässigkeit.** Verwalteter Code wird in einer von der Datenbank-Engine gehosteten Common Language Runtime-Umgebung ausgeführt. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nutzt dies, um eine sicherere Alternative zu den erweiterten gespeicherten Prozeduren zu bieten, die in früheren Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet wurden.  
  
-   **Fähigkeit, Datentypen und Aggregatsfunktionen zu definieren.** Benutzerdefinierte Typen und benutzerdefinierte Aggregate sind zwei neue verwaltete Datenbankobjekte, die die Speicher- und Abfragefunktionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] erweitern.  
  
-   **Rationalisierte Entwicklung durch eine standardisierte Umgebung.** Die Datenbankentwicklung ist in zukünftige Versionen der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio .NET-Entwicklungsumgebung integriert. Entwickler verwenden für das Entwickeln und Debuggen von Datenbankobjekten und Skripts dieselben Tools wie für das Schreiben von .NET Framework-Komponenten und -Diensten auf mittlerer Ebene oder Clientebene.  
  
-   **Potenziell verbesserte Leistung und Skalierbarkeit.** In vielen Situationen sorgen die Kompilierungs- und Ausführungsmodelle der .NET Framework-Sprachen für eine verbesserte Leistungsfähigkeit gegenüber Transact-SQL.  
  
 In der folgenden Tabelle sind die Themen in diesem Abschnitt aufgeführt.  
  
 [Übersicht über die CLR-Integration](clr-integration-overview.md)  
 Beschreibt, welche Objekte mit der CLR-Integration erstellt werden können, und beschreibt die Anforderungen zur Erstellung von Datenbankobjekten mithilfe der CLR-Integration.  
  
 [Neuigkeiten bei der CLR-Integration](clr-integration-what-s-new.md)  
 Beschreibt die neuen Funktionen in dieser Version.  
  
 [Architektur der CLR-Integration](../../database-engine/dev-guide/architecture-of-clr-integration.md)  
 Beschreibt die Entwurfsziele der CLR-Integration.  
  
 [Aktivieren der CLR-Integration](clr-integration-enabling.md)  
 Beschreibt, wie die CLR-Integration aktiviert wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren des .NET Framework](https://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx)   
 [Leistungsfähigkeit der CLR-Integration](clr-integration-architecture-performance.md)  
  
  
