---
title: Transformations-Editor für Suche (Seite ' Fehlerausgabe ') | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.erroroutput.f1
ms.assetid: 15d53bb0-8be1-46fb-b459-04a397e75fac
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 12f1a73c1d21986d2089878bfe9d29dd4450f222
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66057858"
---
# <a name="lookup-transformation-editor-error-output-page"></a>Transformations-Editor für Suche (Seite 'Fehlerausgabe')
  Auf der Seite **Fehlerausgabe** des Dialogfelds **Transformations-Editor für Suche** geben Sie Optionen für die Fehlerbehandlung an.  
  
 Weitere Informationen zur Transformation für Suche finden Sie unter [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Eingabe/Ausgabe**  
 Zeigt den Namen der Eingabe an.  
  
 **Spalte**  
 Wird nicht verwendet.  
  
 **Fehler**  
 Geben Sie an, welche Art von Fehler auftreten soll, wenn Zeilen ohne übereinstimmende Einträge im Verweisdataset behandelt werden:  
  
-   Den Fehler ignorieren und die Zeilen an eine Ausgabe weiterleiten.  
  
-   Die Zeilen an eine Fehlerausgabe weiterleiten.  
  
-   Die Komponente mit einem Fehler abbrechen.  
  
 Diese Option ist nicht verfügbar, wenn Sie in der Liste **Angeben, wie Zeilen ohne übereinstimmende Einträge behandelt werden sollen** den Eintrag **Zeilen an Ausgabe nicht übereinstimmender Einträge umleiten** auswählen. Diese Liste befindet sich auf der Seite **Allgemein** des Dialogfelds **Transformations-Editor für Suche** .  
  
 **Verwandte Themen:** [Fehlerbehandlung in Daten](data-flow/error-handling-in-data.md)  
  
 **Abschneiden**  
 Geben Sie an, was geschehen soll, wenn Daten abgeschnitten werden:  
  
-   Den Fehler ignorieren.  
  
-   Die Zeile umleiten.  
  
-   Die Komponente mit einem Fehler abbrechen.  
  
 **Beschreibung**  
 Zeigt die Beschreibung des Vorgangs an.  
  
 **Ausgewählte Zellen auf diesen Wert festlegen**  
 Geben Sie an, was bei einem Fehler oder beim Abschneiden von Daten mit allen ausgewählten Zellen geschehen soll:  
  
-   Den Fehler ignorieren.  
  
-   Die Zeile umleiten.  
  
-   Die Komponente mit einem Fehler abbrechen.  
  
 **Anwenden**  
 Wendet die Fehlerbehandlungsoption auf die ausgewählten Zellen an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
