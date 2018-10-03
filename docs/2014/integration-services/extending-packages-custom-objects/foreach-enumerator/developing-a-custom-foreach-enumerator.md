---
title: Entwickeln eines benutzerdefinierten Foreach-Enumerators | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
helpviewer_keywords:
- custom foreach enumerators [Integration Services]
- custom foreach enumerators [Integration Services], about custom foreach enumerators
- foreach enumerators [Integration Services]
ms.assetid: bffe26e0-1b9a-47ad-bae6-6b708cb4cf4f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 07df48880932c5e40c2ce8923b87d5c5ddbef876
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48085020"
---
# <a name="developing-a-custom-foreach-enumerator"></a>Entwickeln eines benutzerdefinierten ForEach-Enumerators
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] verwendet Foreach-Enumeratoren, um die Elementen in einer Auflistung zu durchlaufen und die gleichen Tasks für jedes Element auszuführen. [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] enthält eine Vielzahl von Foreach-Enumeratoren, die die am häufigsten verwendeten Auflistungen unterstützen. Dazu gehören alle Dateien in einem Ordner, alle Tabellen in einer Datenbank oder alle Elemente einer in einer Paketvariablen gespeicherten Liste. Sollten die verfügbaren Foreach-Enumeratoren und Auflistungen Ihre Anforderungen nicht vollständig erfüllen, können Sie einen benutzerdefinierten Foreach-Enumerator erstellen.  
  
 Zum Erstellen eines benutzerdefinierten Foreach-Enumerators müssen Sie eine Klasse erstellen, die von der <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>-Basisklasse erbt, das <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>-Attribut auf die neue Klasse anwenden und die Hauptmethoden und -eigenschaften der Basisklasse, einschließlich der <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A>-Methode, überschreiben.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 In diesem Abschnitt wird beschrieben, wie Sie einen benutzerdefinierten Foreach-Enumerator mit zugehöriger Benutzeroberfläche erstellen, konfigurieren und codieren.  
  
 [Erstellen eines benutzerdefinierten Foreach-Enumerators](creating-a-custom-foreach-enumerator.md)  
 Beschreibt die Erstellung der Klassen für ein benutzerdefiniertes Foreach-Enumeratorprojekt.  
  
 [Codieren eines benutzerdefinierten Foreach-Enumerators](coding-a-custom-foreach-enumerator.md)  
 Beschreibt die Implementierung eines benutzerdefinierten Foreach-Enumerators durch Überschreiben der Methoden und Eigenschaften der Basisklasse.  
  
 [Entwickeln einer Benutzeroberfläche für einen benutzerdefinierten ForEach-Enumerator](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
 Beschreibt die Implementierung der Benutzeroberflächenklasse und des Formulars, das für die Konfiguration des benutzerdefinierten Foreach-Enumerators verwendet wird.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
### <a name="information-common-to-all-custom-objects"></a>Informationen, die für alle benutzerdefinierten Objekte gelten  
 Informationen zu allen Arten benutzerdefinierter Objekte, die Sie in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] erstellen können, finden Sie in den folgenden Themen:  
  
 [Entwickeln benutzerdefinierter Objekte für Integration Services](../developing-custom-objects-for-integration-services.md)  
 Beschreibt die grundlegenden Schritte bei der Implementierung aller Typen von benutzerdefinierten Objekten in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 [Beibehalten von benutzerdefinierten Objekten](../persisting-custom-objects.md)  
 Beschreibt die benutzerdefinierte Persistenz und erklärt, wann diese notwendig ist.  
  
 [Erstellen, Bereitstellen und Debuggen von benutzerdefinierten Objekten](../building-deploying-and-debugging-custom-objects.md)  
 Beschreibt die Techniken für das Erstellen, Signieren, Bereitstellen und Debuggen von benutzerdefinierten Objekten.  
  
### <a name="information-about-other-custom-objects"></a>Informationen zu anderen benutzerdefinierten Objekten  
 Informationen zu den anderen Typen benutzerdefinierter Objekte, die Sie in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] erstellen können, finden Sie in den folgenden Themen:  
  
 [Entwickeln eines benutzerdefinierten Tasks](../task/developing-a-custom-task.md)  
 Erläutert die Programmierung benutzerdefinierter Tasks.  
  
 [Entwickeln eines benutzerdefinierten Verbindungs-Managers](../connection-manager/developing-a-custom-connection-manager.md)  
 Erläutert die Programmierung benutzerdefinierter Verbindungs-Manager.  
  
 [Entwickeln eines benutzerdefinierten Protokollanbieters](../log-provider/developing-a-custom-log-provider.md)  
 Erläutert die Programmierung benutzerdefinierter Protokollanbieter.  
  
 [Entwickeln einer benutzerdefinierten Datenflusskomponente](../data-flow/developing-a-custom-data-flow-component.md)  
 Erläutert die Programmierung benutzerdefinierter Datenflussquellen, Transformationen und Ziele.  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
  
