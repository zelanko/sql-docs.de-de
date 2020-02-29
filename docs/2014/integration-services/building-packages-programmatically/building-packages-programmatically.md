---
title: Programmgesteuertes Erstellen von Paketen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 7474b1f4-7607-4f28-a6fd-67f7db1dd3f8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f4227560fbaf3e618a25e3dd214a214ac68a736e
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176555"
---
# <a name="building-packages-programmatically"></a>Programmgesteuertes Erstellen von Paketen
  Wenn Sie Pakete dynamisch erstellen oder [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete außerhalb der Entwicklungsumgebung verwalten und ausführen müssen, können Sie Pakete programmgesteuert ändern. Dieser Ansatz bietet Ihnen eine breite Palette von Optionen:

-   Laden und Ausführen eines vorhandenen Pakets ohne Änderung

-   Laden, Neukonfigurieren (z. B. für eine andere Datenquelle) und Ausführen eines vorhandenen Pakets

-   Erstellen eines neuen Pakets, Hinzufügen und Konfigurieren von Komponenten Objekt um Objekt und Eigenschaft um Eigenschaft, Speichern und Ausführen des Pakets

 Sie können das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Objektmodell verwenden, um in einer beliebigen verwalteten Programmiersprache Code zu schreiben, mit dem Pakete erstellt, konfiguriert und ausgeführt werden. Möglicherweise möchten Sie metadatengesteuerte Pakete erstellen, die ihre Verbindungen oder Datenquellen, Transformationen und Ziele basierend auf der gewählten Datenquelle und ihren Tabellen und Spalten konfigurieren.

 In diesem Abschnitt wird beschrieben und veranschaulicht, wie Pakete programmgesteuert Zeile um Zeile erstellt und konfiguriert werden. Als einfache Möglichkeit der Paketprogrammierung bietet es sich an, ein vorhandenes Paket ohne Änderungen zu laden und auszuführen. Dies wird unter [Programmgesteuerte Ausführung und Verwaltung von Paketen](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md) beschrieben.

 Eine etwas kompliziertere und hier nicht erläuterte Möglichkeit besteht darin, ein vorhandenes Paket als Vorlage zu laden, diese neu zu konfigurieren (beispielsweise für eine andere Datenquelle) und das Paket dann auszuführen. Anhand der Informationen in diesem Abschnitt können Sie auch die vorhandenen Objekte in einem Paket ändern.

> [!NOTE]
>  Wenn Sie ein bestehendes Paket als Vorlage verwenden und vorhandene Spalten im Datenfluss ändern, müssen Sie möglicherweise vorhandene Spalten entfernen und die <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>-Methode der betroffenen Komponenten aufrufen.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Programm gesteuertes Erstellen eines Pakets](../building-packages-programmatically/creating-a-package-programmatically.md) Beschreibt, wie ein Paketprogramm gesteuert erstellt wird.

 [Programm gesteuertes Hinzufügen von Tasks](../building-packages-programmatically/adding-tasks-programmatically.md) Hier wird beschrieben, wie dem Paket Tasks hinzugefügt werden.

 [Programm](../building-packages-programmatically/connecting-tasks-programmatically.md) gesteuertes Verbinden von Tasks Beschreibt, wie die Ausführung von Containern und Tasks in einem Paket basierend auf dem Ergebnis der Ausführung eines vorhergehenden Tasks oder Containers gesteuert wird.

 [Programm gesteuertes Hinzufügen von Verbindungen](../building-packages-programmatically/adding-connections-programmatically.md) Beschreibt, wie Verbindungs-Manager zu einem Paket hinzugefügt werden.

 [Programm gesteuertes arbeiten mit Variablen](../building-packages-programmatically/working-with-variables-programmatically.md) Beschreibt, wie Variablen während der Paket Ausführung hinzugefügt und verwendet werden.

 [Programm](../building-packages-programmatically/handling-events-programmatically.md) gesteuertes behandeln von Ereignissen Beschreibt, wie Paket-und Task Ereignisse behandelt werden.

 [Programm gesteuertes Aktivieren der Protokollierung](../building-packages-programmatically/enabling-logging-programmatically.md) Beschreibt, wie die Protokollierung für ein Paket oder einen Task aktiviert wird und wie benutzerdefinierte Filter auf Protokollereignisse angewendet werden.

 [Programm gesteuertes Hinzufügen des Datenfluss](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md) Tasks Hier wird beschrieben, wie der Datenfluss Task und seine Komponenten hinzugefügt und konfiguriert werden.

 Programm gesteuertes ermitteln von [Datenfluss Komponenten](../building-packages-programmatically/discovering-data-flow-components-programmatically.md) Hier wird beschrieben, wie die auf dem lokalen Computer installierten Komponenten erkannt werden.

 [Programm gesteuertes Hinzufügen von Datenfluss Komponenten](../building-packages-programmatically/adding-data-flow-components-programmatically.md) Beschreibt das Hinzufügen einer Komponente zu einem Datenfluss Task.

 [Programm gesteuertes Verbinden von Datenfluss Komponenten](../building-packages-programmatically/connecting-data-flow-components-programmatically.md) Beschreibt, wie zwei Datenfluss Komponenten verbunden werden.

 [Programm gesteuertes auswählen von Eingabe Spalten](../building-packages-programmatically/selecting-input-columns-programmatically.md) Beschreibt, wie Eingabe Spalten aus denjenigen ausgewählt werden, die einer Komponente von Upstreamkomponenten im Datenfluss bereitgestellt werden.

 [Programm gesteuertes Speichern eines Pakets](../building-packages-programmatically/saving-a-package-programmatically.md) Hier wird beschrieben, wie ein Paketprogramm gesteuert gespeichert wird.

## <a name="reference"></a>Verweis
 [Fehler-und](../integration-services-error-and-message-reference.md) Meldungs Referenz für Integration Services Listet die vordefinierten [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Fehlercodes mit ihren symbolischen Namen und Beschreibungen auf.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Erweitern von Paketen mit](../extending-packages-scripting/extending-packages-with-scripting.md) Skripts Erläutert, wie die Ablauf Steuerung mithilfe des Skript Tasks erweitert wird und wie der Datenfluss mithilfe der Skript Komponente erweitert wird.

 [Erweitern von Paketen mit benutzerdefinierten Objekten](../extending-packages-custom-objects/extending-packages-with-custom-objects.md) Erläutert, wie benutzerdefinierte Programm Tasks, Datenfluss Komponenten und andere Paket Objekte für die Verwendung in mehreren Paketen erstellt werden.

 [Programm gesteuertes ausführen und Verwalten von Paketen](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md) Erläutert, wie Pakete und die Ordner, in denen Sie gespeichert sind, aufgezählt, ausgeführt und verwaltet werden.

## <a name="external-resources"></a>Externe Ressourcen

-   CodePlex-Beispiele, [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkID=131204), auf www.codeplex.com/MSFTISProdSamples

-   Blogeintrag [Leistungsprofilerstellung für benutzerdefinierte Erweiterungen](https://go.microsoft.com/fwlink/?LinkId=238831)auf blogs.msdn.com.

![Integration Services Symbol (klein)](../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.

## <a name="see-also"></a>Weitere Informationen
 [SQL Server Integration Services](../sql-server-integration-services.md)


