---
title: Entwickeln einer benutzerdefinierten Datenflusskomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], extending
- data flow [Integration Services], extending
- extending data flow task [Integration Services]
- components [Integration Services], data flow
ms.assetid: be126913-2a9a-41c9-9bf5-a7b0a0aea2f8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6121149433cd0f687c91663f7bb1b23ecb38aaff
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53369472"
---
# <a name="developing-a-custom-data-flow-component"></a>Entwickeln einer benutzerdefinierten Datenflusskomponente
  Die Datenflusstask besteht aus Komponenten, die eine Verbindung zu einer Reihe von Datenquellen herstellen und die Daten dann mit Hochgeschwindigkeit transformieren und routen. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] stellt ein erweiterbares Objektmodell bereit, mit dem Entwickler benutzerdefinierte Quellen, Transformationen und Ziele erstellen können, die in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] und in bereitgestellten Paketen Verwendung finden. Dieser Abschnitt enthält Themen, die Sie durch die Entwicklung benutzerdefinierter Datenflusskomponenten führen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erstellen einer benutzerdefinierten Datenflusskomponente](creating-a-custom-data-flow-component.md)  
 Erläutert die ersten Schritte zum Erstellen einer benutzerdefinierten Datenflusskomponente.  
  
 [Entwurfszeitmethoden einer Datenflusskomponente](design-time-methods-of-a-data-flow-component.md)  
 Erläutert die Entwurfszeitmethoden, die in eine benutzerdefinierte Datenflusskomponente implementiert werden sollen.  
  
 [Laufzeitmethoden einer Datenflusskomponente](run-time-methods-of-a-data-flow-component.md)  
 Erläutert die Laufzeitmethoden, die in eine benutzerdefinierte Datenflusskomponente implementiert werden sollen.  
  
 [Ausführungsplan und Pufferzuordnung](execution-plan-and-buffer-allocation.md)  
 Erläutert den Datenfluss-Ausführungsplan und die Zuordnung von Datenpuffern.  
  
 [Verwenden von Datentypen im Datenfluss](working-with-data-types-in-the-data-flow.md)  
 Erklärt, wie der Datenfluss von .NET Framework verwalteten Daten [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Datentypen zuordnet.  
  
 [Überprüfen einer Datenflusskomponente](validating-a-data-flow-component.md)  
 Erklärt die Methoden, mit denen die Komponentenkonfiguration überprüft und Komponentenmetadaten neu konfiguriert werden.  
  
 [Implementieren externer Metadaten](implementing-external-metadata.md)  
 Erklärt, wie Daten mit externen Metadatenspalten überprüft werden.  
  
 [Auslösen und Definieren von Ereignissen in einer Datenflusskomponente](raising-and-defining-events-in-a-data-flow-component.md)  
 Erklärt, wie vordefinierte und benutzerdefinierte Ereignisse ausgelöst werden.  
  
 [Protokollieren und Definieren von Protokolleinträgen in einer Datenflusskomponente](logging-and-defining-log-entries-in-a-data-flow-component.md)  
 Erklärt, wie benutzerdefinierte Protokolleinträge erstellt und hinzugefügt werden.  
  
 [Verwenden von Fehlerausgaben in einer Datenflusskomponente](using-error-outputs-in-a-data-flow-component.md)  
 Erklärt, wie Fehlerzeilen zu einer alternativen Ausgabe umgeleitet werden.  
  
 [Aktualisieren der Version einer Datenflusskomponente](upgrading-the-version-of-a-data-flow-component.md)  
 Erklärt, wie gespeicherte Komponentenmetadaten aktualisiert werden, wenn eine neue Version der Komponente zuerst verwendet wird.  
  
 [Entwickeln einer Benutzeroberfläche für eine Datenflusskomponente](developing-a-user-interface-for-a-data-flow-component.md)  
 Erklärt, wie ein benutzerdefinierter Editor für eine Komponente implementiert wird.  
  
 [Entwickeln bestimmter Arten von Datenflusskomponenten](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
 Enthält Informationen zum Entwickeln der drei Arten von Datenflusskomponenten: Quellen, Transformationen und Ziele.  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.SqlServer.Dts.Pipeline>  
 Enthält die Klassen und Schnittstellen zur Erstellung benutzerdefinierter Datenflusskomponenten.  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>  
 Enthält die Klassen und Schnittstellen, aus denen sich das Objektmodell des Datenflusstasks zusammensetzt, und wird zum Erstellen benutzerdefinierter Datenflusskomponenten oder eines Datenflusstasks verwendet.  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Design>  
 Enthält die Klassen und Schnittstellen zur Erstellung der Benutzeroberfläche für Datenflusskomponenten.  
  
 [Fehler- und Meldungsreferenz von Integration Services](../../integration-services-error-and-message-reference.md)  
 Listet die vordefinierten [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Fehlercodes mit ihren symbolischen Namen und Beschreibungen auf.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
  
### <a name="information-common-to-all-custom-objects"></a>Informationen, die für alle benutzerdefinierten Objekte gelten  
 Informationen zu allen Arten benutzerdefinierter Objekte, die Sie in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] erstellen können, finden Sie in den folgenden Themen:  
  
 [Entwickeln benutzerdefinierter Objekte für Integration Services](../../extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)  
 Beschreibt die grundlegenden Schritte bei der Implementierung aller Typen von benutzerdefinierten Objekten in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 [Beibehalten von benutzerdefinierten Objekten](../../extending-packages-custom-objects/persisting-custom-objects.md)  
 Beschreibt die benutzerdefinierte Persistenz und erklärt, wann diese notwendig ist.  
  
 [Erstellen, Bereitstellen und Debuggen von benutzerdefinierten Objekten](../../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)  
 Beschreibt die Techniken für das Erstellen, Signieren, Bereitstellen und Debuggen von benutzerdefinierten Objekten.  
  
### <a name="information-about-other-custom-objects"></a>Informationen zu anderen benutzerdefinierten Objekten  
 Informationen zu den anderen Typen benutzerdefinierter Objekte, die Sie in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] erstellen können, finden Sie in den folgenden Themen:  
  
 [Entwickeln eines benutzerdefinierten Tasks](../../extending-packages-custom-objects/task/developing-a-custom-task.md)  
 Erläutert die Programmierung benutzerdefinierter Tasks.  
  
 [Entwickeln eines benutzerdefinierten Verbindungs-Managers](../../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)  
 Erläutert die Programmierung benutzerdefinierter Verbindungs-Manager.  
  
 [Entwickeln eines benutzerdefinierten Protokollanbieters](../../extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md)  
 Erläutert die Programmierung benutzerdefinierter Protokollanbieter.  
  
 [Entwickeln eines benutzerdefinierten ForEach-Enumerators](../../extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 Erläutert die Programmierung benutzerdefinierter Enumeratoren.  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern des Datenflusses mit der Skriptkomponente] (.. /.. /Extending-Packages-Scripting/Data-Flow-Script-Component/Extending-the-Data-Flow-with-the-Script-Component.MD   
 [Vergleichen von Skriptlösungen und benutzerdefinierten Objekten](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)  
  
  
