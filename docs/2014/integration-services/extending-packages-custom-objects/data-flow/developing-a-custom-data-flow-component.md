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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 061daaa3b44c151a1f77b075bef66ef90570af98
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176348"
---
# <a name="developing-a-custom-data-flow-component"></a>Entwickeln einer benutzerdefinierten Datenflusskomponente
  Die Datenflusstask besteht aus Komponenten, die eine Verbindung zu einer Reihe von Datenquellen herstellen und die Daten dann mit Hochgeschwindigkeit transformieren und routen. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] stellt ein erweiterbares Objektmodell bereit, mit dem Entwickler benutzerdefinierte Quellen, Transformationen und Ziele erstellen können, die Sie in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] und in bereitgestellten Paketen verwenden können. Dieser Abschnitt enthält Themen, die Sie durch die Entwicklung benutzerdefinierter Datenflusskomponenten führen.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Erstellen einer benutzerdefinierten Datenfluss Komponente](creating-a-custom-data-flow-component.md) Beschreibt die ersten Schritte beim Erstellen einer benutzerdefinierten Datenfluss Komponente.

 [Entwurfszeit Methoden einer Datenfluss Komponente](design-time-methods-of-a-data-flow-component.md) Beschreibt die Entwurfszeit Methoden, die in einer benutzerdefinierten Datenfluss Komponente implementiert werden sollen.

 [Lauf Zeit Methoden einer Datenfluss Komponente](run-time-methods-of-a-data-flow-component.md) Beschreibt die Lauf Zeit Methoden, die in einer benutzerdefinierten Datenfluss Komponente implementiert werden sollen.

 [Ausführungs Plan und Puffer Zuordnung](execution-plan-and-buffer-allocation.md) Beschreibt den Datenfluss-Ausführungsplan und die Zuordnung von Daten Puffern.

 [Arbeiten mit Datentypen im Datenfluss](working-with-data-types-in-the-data-flow.md) Erläutert, wie der Datenfluss [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .NET Framework verwalteten Datentypen Datentypen zuordnet.

 [Validieren einer Datenfluss Komponente](validating-a-data-flow-component.md) Erläutert die Methoden, die zum Überprüfen der Komponenten Konfiguration und zum Neukonfigurieren von Komponenten Metadaten verwendet werden.

 [Implementieren externer Metadaten](implementing-external-metadata.md) Erläutert, wie externe Metadatenspalten für die Datenvalidierung verwendet werden.

 [Erhöhen und Definieren von Ereignissen in einer Datenfluss Komponente](raising-and-defining-events-in-a-data-flow-component.md) Erläutert, wie vordefinierte und benutzerdefinierte Ereignisse angehoben werden.

 [Protokollieren und Definieren von Protokoll Einträgen in einer Datenfluss Komponente](logging-and-defining-log-entries-in-a-data-flow-component.md) Erläutert, wie benutzerdefinierte Protokolleinträge erstellt und geschrieben werden.

 [Verwenden von Fehler Ausgaben in einer Datenfluss Komponente](using-error-outputs-in-a-data-flow-component.md) Erläutert, wie Fehler Zeilen an eine Alternative Ausgabe umgeleitet werden.

 [Aktualisieren der Version einer Datenfluss Komponente](upgrading-the-version-of-a-data-flow-component.md) Erläutert, wie gespeicherte Komponenten Metadaten aktualisiert werden, wenn eine neue Version der Komponente verwendet wird.

 [Entwickeln einer Benutzeroberfläche für eine Datenfluss Komponente](developing-a-user-interface-for-a-data-flow-component.md) Erläutert, wie ein benutzerdefinierter Editor für eine Komponente implementiert wird.

 [Entwickeln bestimmter Typen von Datenfluss Komponenten](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md) Enthält Informationen zum Entwickeln der drei Arten von Datenfluss Komponenten: Quellen, Transformationen und Ziele.

## <a name="reference"></a>Verweis
 <xref:Microsoft.SqlServer.Dts.Pipeline>Enthält die Klassen und Schnittstellen, die zum Erstellen von benutzerdefinierten Datenfluss Komponenten verwendet werden.

 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>Enthält die Klassen und Schnittstellen, die das Datenfluss Task-Objektmodell bilden, und wird zum Erstellen benutzerdefinierter Datenfluss Komponenten oder zum Erstellen eines Datenfluss Tasks verwendet.

 <xref:Microsoft.SqlServer.Dts.Pipeline.Design>Enthält die Klassen und Schnittstellen, die zum Erstellen der Benutzeroberfläche für Datenfluss Komponenten verwendet werden.

 [Fehler-und](../../integration-services-error-and-message-reference.md) Meldungs Referenz für Integration Services Listet die vordefinierten [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Fehlercodes mit ihren symbolischen Namen und Beschreibungen auf.

## <a name="related-sections"></a>Verwandte Abschnitte

### <a name="information-common-to-all-custom-objects"></a>Informationen, die für alle benutzerdefinierten Objekte gelten
 Informationen zu allen Arten benutzerdefinierter Objekte, die Sie in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] erstellen können, finden Sie in den folgenden Themen:

 [Entwickeln von benutzerdefinierten Objekten für Integration Services](../../extending-packages-custom-objects/developing-custom-objects-for-integration-services.md) Beschreibt die grundlegenden Schritte zum Implementieren aller Typen von benutzerdefinierten [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]Objekten für.

 Beibehalten von [benutzerdefinierten Objekten](../../extending-packages-custom-objects/persisting-custom-objects.md) Beschreibt die benutzerdefinierte Persistenz und erläutert, wann dies notwendig ist.

 Entwickeln, bereitstellen [und Debuggen von benutzerdefinierten Objekten](../../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md) Beschreibt die Techniken zum entwickeln, signieren, bereitstellen und Debuggen von benutzerdefinierten Objekten.

### <a name="information-about-other-custom-objects"></a>Informationen zu anderen benutzerdefinierten Objekten
 Informationen zu den anderen Typen benutzerdefinierter Objekte, die Sie in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] erstellen können, finden Sie in den folgenden Themen:

 [Entwickeln eines benutzerdefinierten](../../extending-packages-custom-objects/task/developing-a-custom-task.md) Tasks Erläutert, wie benutzerdefinierte Tasks programmiert werden.

 [Entwickeln eines benutzerdefinierten Verbindungs-Managers](../../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md) Erläutert, wie benutzerdefinierte Verbindungs-Manager programmiert werden.

 [Entwickeln eines benutzerdefinierten Protokoll Anbieters](../../extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md) Erläutert, wie benutzerdefinierte Protokoll Anbieter programmiert werden.

 [Entwickeln eines benutzerdefinierten Foreach-Enumerators](../../extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md) Erläutert, wie benutzerdefinierte Enumeratoren programmiert werden.

![Integration Services Symbol (klein)](../../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.

## <a name="see-also"></a>Weitere Informationen
 [Erweitern des Datenflusses mit der Skript Komponente] (.. /.. /Extending-Packages-Scripting/Data-Flow-Script-Component/Extending-the-Data-Flow-with-the-Script-Component.MD [Vergleichen von Skript Lösungen und benutzerdefinierten Objekten](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)


