---
title: OLAP-Engine-Serverkomponenten | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 535d1e05fc82882e0a2b5ea43ac9b2147e62338b
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388019"
---
# <a name="olap-engine-server-components"></a>OLAP-Engine-Serverkomponenten
  Die Serverkomponente [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] der Anwendung **msmdsrv.exe,** die als Windows-Dienst ausgeführt wird. Diese Anwendung besteht aus Sicherheitskomponenten, einer XMLA-Überwachungskomponente (XML for Analysis), einer Abfrageverarbeitungskomponente und zahlreichen internen Komponenten, die die folgenden Funktionen ausführen:

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
 Die XMLA-Überwachungskomponente verarbeitet die gesamte XMLA-Kommunikation zwischen [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] und den zugehörigen Clients. Die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` Konfigurationseinstellung in der Datei msmdsrv.ini kann verwendet [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] werden, um einen Port anzugeben, auf dem eine Instanz lauscht. Wird in dieser Datei der Wert 0 angegeben, wird der Standardport von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] überwacht. Falls nicht anders angegeben, verwendet [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] die folgenden TCP-Standardports:

|Port|BESCHREIBUNG|
|----------|-----------------|
|2383|Standardinstanz [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]von .|
|2382|Redirector für andere [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]Instanzen von .|
|Dynamische Zuweisung beim Serverstart.|Benannte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]Instanz von .|

 Weitere Informationen finden Sie unter [Konfigurieren der Windows-Firewall zum Zulassen](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) des Zugriffs auf Analysis Services.

## <a name="see-also"></a>Weitere Informationen
 [Objektbenennungsregeln &#40;Analysis Services&#41;](object-naming-rules-analysis-services.md) Physical Architecture &#40;Analysis Services - [Multidimensional Data&#41;](understanding-microsoft-olap-physical-architecture.md) Logical Architecture &#40;Analysis Services - [Multidimensional Data&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)


