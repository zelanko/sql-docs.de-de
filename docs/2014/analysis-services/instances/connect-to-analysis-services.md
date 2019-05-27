---
title: Verbinden von Analysis Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- instances of Analysis Services, connections
ms.assetid: 73ee8171-3379-4384-bfc8-071b3eebbc8f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 654d659900d01ae9d5caf5188b9146510de483ec
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66080121"
---
# <a name="connect-to-analysis-services"></a>Verbindung mit Analysis Services herstellen
  In diesem Abschnitt erfahren Sie etwas über Eigenschaften von Verbindungszeichenfolgen, Clientbibliotheken für Verbindungen, die von Analysis Services unterstützten Authentifizierungsmethoden sowie das Einrichten oder Löschen von Verbindungen, bevor ein Server offline geschaltet wird.  
  
## <a name="analysis-services-connections"></a>Analysis Services-Verbindungen  
 Analysis Services verwendet TCP als Netzwerkprotokoll und XML for Analysis (XMLA) als Kommunikationsprotokoll. Auf der untersten Ebene wird von allen Clientbibliotheken, die mit Analysis Services bereitgestellt wurden, XMLA-over-TCP implementiert. Obwohl es möglich ist, Anwendungen auf Grundlage der XMLA-Struktur zu erstellen, verwenden die meisten Anwendungen und Anwendungsentwickler Clientbibliotheken, um die Vorteile von Objektmodellen und die damit verbundene effiziente Codierung zu nutzen. Für Clientverbindungen zu Analysis Services können Sie IIS als zwischengeschaltete Verbindung verwenden, wenn Sie TCP nicht über den Stapel hinweg verwenden können. Ein Vorteil der Verwendung von HTTP-Zugriff über IIS ist die Möglichkeit, eine Verbindung von Anwendungen aus herzustellen, die Anmeldeinformationen in der Verbindungszeichenfolge übergeben.  
  
 In Zusammenhang mit Konnektivität geht es immer auch um Authentifizierung. Im Unterschied zu anderen SQL Server-Funktionen verwendet Analysis Services ausschließlich die Windows-Anmeldeinformationen. Es ist nicht möglich, auf der Back-End-Verbindung mit Analysis Services die SQL Server-Datenbankauthentifizierung, die Forderungsauthentifizierung, die formularbasierte Authentifizierung oder Digest zu verwenden. Weitere Informationen zur Authentifizierung finden Sie in diesem Abschnitt.  
  
##  <a name="bkmk_clientApps"></a> Verbindungsaufgaben  
  
|Link|Taskbeschreibung|  
|----------|----------------------|  
|[Herstellen einer Verbindung von Clientanwendungen &#40;Analysis Services&#41;](connect-from-client-applications-analysis-services.md)|Wenn Sie mit Analysis Services nicht vertraut sind, lesen Sie dieses Thema, um sich einen Überblick über die Tools und Anwendungen zu verschaffen, die am häufigsten mit Analysis Services verwendet werden.|  
|[Verbindungszeichenfolgen-Eigenschaften &#40;Analysis Services&#41;](connection-string-properties-analysis-services.md)|Analysis Services umfasst zahlreiche Server- und Datenbankeigenschaften, mit denen eine Verbindung unabhängig davon, wie die Instanz oder Datenbank konfiguriert ist, an spezifische Anwendungen angepasst werden kann.|  
|[Von Analysis Services unterstützte Authentifizierungsmethoden](authentication-methodologies-supported-by-analysis-services.md)|Dieses Thema gibt eine kurze Einführung in die Authentifizierungsmethoden, die von Analysis Services verwendet werden.|  
|[Konfigurieren von Analysis Services für die eingeschränkte Kerberos-Delegierung](configure-analysis-services-for-kerberos-constrained-delegation.md)|Viele Business Intelligence-Lösungen setzen den Identitätswechsel voraus, um sicherzustellen, dass nur berechtigte Daten an die einzelnen Benutzer zurückgegeben werden. In diesem Thema werden die Voraussetzungen für die Verwendung des Identitätswechsels beschrieben. In diesem Thema werden außerdem die Schritte zum Konfigurieren von Analysis Services für die eingeschränkte Kerberos-Delegierung beschrieben.|  
|[SPN-Registrierung für eine Analysis Services-Instanz](spn-registration-for-an-analysis-services-instance.md)|Die Kerberos-Authentifizierung setzt einen gültigen Dienstprinzipalnamen (Service Principal Name, SPN) für Dienste voraus, durch die die Identität eines Benutzers in einer Multiserverlösung angenommen oder delegiert wird. Verwenden Sie die Informationen in diesem Thema, um mehr darüber zu erfahren, wie Sie die SPN-Registrierung für Analysis Services erstellen und ausführen.|  
|[Konfigurieren von HTTP-Zugriff auf Analysis Services unter Internetinformationsdienste &#40;IIS&#41; 8.0](configure-http-access-to-analysis-services-on-iis-8-0.md)|Standardauthentifizierung oder domänenübergreifende Nutzung sind zwei wichtige Gründe, um Analysis Services für den HTTP-Zugriff zu konfigurieren.|  
|[Für Analysis Services-Verbindungen verwendete Datenanbieter](data-providers-used-for-analysis-services-connections.md)|Analysis Services stellt drei Clientbibliotheken für den Zugriff auf Servervorgänge oder Analysis Services-Daten bereit. Dieses Thema enthält eine kurze Einführung zu ADOMD.NET, AMOs (Analysis Services Management Objects) und dem OLE DB-Anbieter für Analysis Services (MSOLAP).|  
|[Trennen von Benutzern und Sitzungen auf Analysis Services-Server](disconnect-users-and-sessions-on-analysis-services-server.md)|Löschen Sie vorhandene Verbindungen und Sitzungen, bevor Sie einen Server offline schalten oder Baseline-Leistungstests durchführen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konfiguration nach der Installation &#40;Analysis Services&#41;](post-install-configuration-analysis-services.md)   
 [Konfigurieren von Servereigenschaften in Analysis Services](../server-properties/server-properties-in-analysis-services.md)   
 [Skriptverwaltungsaufgaben in Analysis Services](../script-administrative-tasks-in-analysis-services.md)  
  
  
