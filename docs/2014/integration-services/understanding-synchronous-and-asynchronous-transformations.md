---
title: Grundlegendes zu synchronen und asynchronen Transformationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- transformations [Integration Services], synchronous and asynchronous
- asynchronous transformations [Integration Services]
- data flow components [Integration Services], synchronous and asynchronous
- synchronous transformations [Integration Services]
ms.assetid: 0bc2bda5-3f8a-49c2-aaf1-01dbe4c3ebba
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3d18f66d3522aa072993bd602dad7e19951de5eb
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85420407"
---
# <a name="understanding-synchronous-and-asynchronous-transformations"></a>Grundlegendes zu synchronen und asynchronen Transformationen
  Den Unterschied zwischen einer synchronen und asynchronen Transformation in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] versteht man am besten, wenn man die Grundzüge einer synchronen Transformation kennt. Wenn eine synchrone Transformation Ihre Anforderungen nicht erfüllt, könnte Ihr Design eine asynchrone Transformation erfordern.

## <a name="synchronous-transformations"></a>Synchrone Transformationen
 Bei einer synchronen Transformation werden eingehende Zeilen verarbeitet und zeilenweise in den Datenfluss übergeben. Die Ausgabe ist mit der Eingabe synchron, erfolgt demnach gleichzeitig. Deshalb werden bei der Transformation zur Verarbeitung einer bestimmten Zeile keine Informationen über andere Zeilen im Dataset benötigt. In der eigentlichen Bereitstellung werden Zeilen bei der Weitergabe von einer Komponente zur nächsten in Puffern gruppiert, die jedoch für den Benutzer transparent sind; man kann davon ausgehen, dass jede Zeile separat verarbeitet wird.

 Ein Beispiel für eine synchrone Transformation ist die Transformation für Datenkonvertierung. Für jede eingehende Zeile wird der Wert in der angegebenen Spalte konvertiert und dann die Zeile weitergesendet. Jeder einzelne Konvertierungsvorgang ist von allen anderen Zeilen im Dataset unabhängig.

 Bei der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Skripterstellung und Programmierung geben Sie eine synchrone Transformation an, indem Sie die ID der Eingabe einer Komponente suchen und Sie der `SynchronousInputID` -Eigenschaft der Ausgaben der Komponente zuweisen. Dadurch wird die Datenfluss-Engine angewiesen, jede Zeile aus der Eingabe zu verarbeiten und jede Zeile automatisch an angegebene Ausgaben zu senden. Wenn Sie möchten, dass jede Zeile an jede Ausgabe gesendet wird, brauchen Sie keinen zusätzlichen Code für die Ausgabe der Daten zu schreiben. Wenn Sie mit der `ExclusionGroup`-Eigenschaft angeben, dass Zeilen nur an bestimmte Ausgabegruppen gesendet werden sollen, wie bei der Transformation für bedingtes Teilen, müssen Sie die `DirectRow`-Methode aufrufen, um das jeweilige Ziel für die einzelnen Zeilen auszuwählen. Bei einer Fehlerausgabe müssen Sie `DirectErrorRow` aufrufen, um Zeilen mit Problemen an die Fehlerausgabe, und nicht an die Standardausgabe zu senden.

## <a name="asynchronous-transformations"></a>Asynchrone Transformationen
 Möglicherweise erfordert Ihr Design eine asynchrone Transformation, wenn die Verarbeitung der einzelnen Zeilen unabhängig von allen anderen Zeilen nicht möglich ist. Anders ausgedrückt, können Sie nicht jede Zeile bei der Verarbeitung an den Datenfluss weitergeben, sondern müssen Daten asynchron bzw. zu einer anderen Zeit als die Eingabe ausgeben. Zum Beispiel erfordern die folgenden Szenarios eine asynchrone Transformation:

-   Die Komponente muss mehrere Datenpuffer abrufen, bevor die Verarbeitung ausgeführt werden kann. Ein Beispiel ist die Transformation zum Sortieren, bei der die Komponente den vollständigen Satz an Zeilen in einem Vorgang verarbeiten muss.

-   Die Komponente muss Zeilen mehrerer Eingaben kombinieren. Ein Beispiel ist die Transformation für Zusammenführen, bei der die Komponente mehrere Zeilen jeder Eingabe überprüfen und sie anschließend in sortierter Reihenfolge zusammenführen muss.

-   Es gibt keine 1:1-Entsprechung zwischen Eingabezeilen und Ausgabezeilen. Ein Beispiel ist die Transformation für das Aggregieren, bei der die Komponente eine Zeile zur Ausgabe hinzufügen muss, um die berechneten Aggregatwerte aufzunehmen.

 Bei der Skripterstellung und Programmierung in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] geben Sie eine asynchrone Transformation an, indem Sie den Wert 0 zur `SynchronousInputID`-Eigenschaft der Ausgaben der Komponente zuweisen. erforderlich. Dadurch wird die Datenfluss-Engine angewiesen, nicht jede Zeile automatisch an die Ausgaben zu senden. Anschließend müssen Sie den Code schreiben, um jede Zeile explizit an die jeweilige Ausgabe zu senden, indem sie dem neuen Ausgabepuffer hinzugefügt wird, der für die Ausgabe einer asynchronen Transformation erstellt wird.

> [!NOTE]
>  Da eine Quellkomponente auch jede Zeile, die aus der Datenquelle gelesen wird, explizit ihren Ausgabepuffern hinzufügen muss, ähnelt eine Quelle einer Transformation mit asynchronen Ausgaben.

 Es wäre auch mögliche, eine asynchrone Transformation zu erstellen, die eine synchrone Transformation emuliert, indem man jede Eingabezeile explizit in die Ausgabe kopiert. Mit diesem Ansatz könnten Sie Spalten umbenennen oder Datentypen oder -formate konvertieren. Dieser Ansatz beeinträchtigt jedoch die Leistung. Sie können die gleichen Ergebnisse bei besserer Leistung erreichen, indem Sie eingebaute Integration Services-Komponenten verwenden, wie zum Beispiel Kopieren von Spalten oder Datenkonvertierung.

![Integration Services Symbol (klein)](media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.

## <a name="see-also"></a>Weitere Informationen
 [Erstellen einer synchronen Transformation mit der Skript Komponente](data-flow/transformations/script-component.md) [Erstellen einer asynchronen Transformation mit der Skript Komponente](extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md) [Entwickeln einer benutzerdefinierten Transformations Komponente mit synchronen Ausgaben](extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md) [Entwickeln einer benutzerdefinierten Transformations Komponente mit asynchronen Ausgaben](extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)


