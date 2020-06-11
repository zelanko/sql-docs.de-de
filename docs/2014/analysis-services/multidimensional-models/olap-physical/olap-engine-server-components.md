---
title: OLAP-Engine-Server Komponenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- ports [Analysis Services]
- XML/A listener
- server architecture [Analysis Services]
ms.assetid: 5193c976-9dcd-459c-abba-8c3c44e7a7f2
author: minewiskan
ms.author: owend
ms.openlocfilehash: b60d721a69213ad52536830b49b40d6bb82a3811
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545912"
---
# <a name="olap-engine-server-components"></a>OLAP-Engine-Serverkomponenten
  Die Serverkomponente von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ist die **msmdsrv.exe** Anwendung, die als Windows-Dienst ausgeführt wird. Diese Anwendung besteht aus Sicherheitskomponenten, einer XMLA-Überwachungskomponente (XML for Analysis), einer Abfrageverarbeitungskomponente und zahlreichen internen Komponenten, die die folgenden Funktionen ausführen:

-   Analysieren von Anweisungen, die von Client empfangen werden

-   Verwalten von Metadaten

-   Behandeln von Transaktionen

-   Verarbeiten von Berechnungen

-   Speichern von Dimensions- und Zellendaten

-   Erstellen von Aggregationen

-   Planen von Abfragen

-   Zwischenspeichern von Objekten

-   Verwalten von Serverressourcen

## <a name="architectural-diagram"></a>Architekturdiagramm
 Eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Instanz wird als eigenständiger Dienst ausgeführt, und die Kommunikation mit dem Dienst erfolgt in XMLA (XML for Analysis) über HTTP oder TCP. AMO ist eine Ebene zwischen der Benutzeranwendung und der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz. Diese Ebene bietet Zugriff auf [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Verwaltungsobjekte. AMO ist eine Klassenbibliothek, die Befehle von Clientanwendungen entgegennimmt und diese Befehle in XMLA-Nachrichten für die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Instanz übersetzt. AMO stellt Objekte der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Instanz für die Endbenutzerumgebung als Klassen dar, wobei Methodenmember Befehle ausführen und Eigenschaftenmember die Daten für die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Objekte speichern.

 Die folgende Abbildung stellt die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Komponentenarchitektur dar, einschließlich aller wichtigen Elemente, die in der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz ausgeführt werden, und aller Benutzerkomponenten, die mit der Instanz zusammenarbeiten. Diese Abbildung zeigt auch, dass nur mit dem XMLA (XML for Analysis)-Listener entweder über HTTP oder TCP auf die Instanz zugegriffen werden kann.

 ![Analysis Services-Systemarchitektur (Diagramm)](../../../analysis-services/dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services-Systemarchitektur (Diagramm)")

## <a name="xmla-listener"></a>XMLA-Überwachung
 Die XMLA-Überwachungskomponente verarbeitet die gesamte XMLA-Kommunikation zwischen [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] und den zugehörigen Clients. Die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` Konfigurationseinstellung in der msmdsrv.ini-Datei kann verwendet werden, um einen Port anzugeben, auf dem eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz lauscht. Wird in dieser Datei der Wert 0 angegeben, wird der Standardport von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] überwacht. Falls nicht anders angegeben, verwendet [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] die folgenden TCP-Standardports:

|Port|Beschreibung|
|----------|-----------------|
|2383|Standard Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .|
|2382|Redirector für andere Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .|
|Dynamische Zuweisung beim Serverstart.|Benannte Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .|

 Weitere Informationen finden [Sie unter Konfigurieren der Windows-Firewall, um Analysis Services Zugriff zuzulassen](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) .

## <a name="see-also"></a>Weitere Informationen
 [Benennungs Regeln für Objekte &#40;Analysis Services&#41;](object-naming-rules-analysis-services.md) [physische Architektur &#40;Analysis Services von mehrdimensionalen Daten&#41;](understanding-microsoft-olap-physical-architecture.md) [logische Architektur &#40;Analysis Services-mehrdimensionalen Daten&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)


