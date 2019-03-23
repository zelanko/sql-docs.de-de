---
title: Quellen-Editor für CDC (Seite Fehlerausgabe) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.errorhandling.f1
ms.assetid: 8a4c2cb8-fd2f-4c45-824f-b93473a8981e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4a5a98644dc9c8f887b72cd5cc76c1d7c38ae174
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58389308"
---
# <a name="cdc-source-editor-error-output-page"></a>Quellen-Editor für CDC (Seite Fehlerausgabe)
  Auf der Seite **Fehlerausgabe** des Dialogfelds **Quellen-Editor für CDC** können Sie Optionen für die Fehlerbehandlung auswählen.  
  
 Weitere Informationen zur CDC-Quelle finden Sie unter [CDC Source](data-flow/cdc-source.md).  
  
## <a name="task-list"></a>Aufgabenliste  
 **So öffnen Sie die Seite "Fehlerausgabe" des Quellen-Editors für CDC**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]das [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] -Paket, das die CDC-Quelle enthält.  
  
2.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf die CDC-Quelle.  
  
3.  Klicken Sie im **Quellen-Editor für CDC**auf **Fehlerausgabe**.  
  
## <a name="options"></a>Optionen  
 **Eingabe/Ausgabe**  
 Zeigt den Namen der Datenquelle an.  
  
 **Column**  
 Zeigt die externen Spalten (Quellspalten) an, die im Dialogfeld **Quellen-Editor für CDC** auf der Seite **Verbindungs-Manager** ausgewählt wurden.  
  
 **Fehler**  
 Wählen Sie aus, wie die CDC-Quelle Fehler in einem Fluss behandeln soll: Fehler ignorieren, Zeile umleiten oder Komponente mit einem Fehler abbrechen.  
  
 **Abschneiden**  
 Wählen Sie aus, wie die CDC-Quelle Kürzungen in einem Fluss behandeln soll: Fehler ignorieren, Zeile umleiten oder Komponente mit einem Fehler abbrechen.  
  
 **Beschreibung**  
 Wird nicht verwendet.  
  
 **Diesen Wert für ausgewählte Zellen festlegen**  
 Wählen Sie aus, wie die CDC-Quelle im Fall eines Fehlers oder einer Kürzung mit den ausgewählten Zellen verfahren soll: Fehler ignorieren, Zeile umleiten oder Komponente mit einem Fehler abbrechen.  
  
 **Anwenden**  
 Wendet die Fehlerbehandlungsoptionen auf die ausgewählten Zellen an.  
  
## <a name="error-handling-options"></a>Fehlerbehandlungsoptionen  
 Mit den folgenden Optionen konfigurieren Sie, wie die CDC-Quelle Fehler und Kürzungen behandelt.  
  
 **Fehler bei Komponente**  
 Bei einem Fehler oder beim Abschneiden von Daten wird der Datenflusstask nicht ausgeführt. Dies ist das Standardverhalten.  
  
 **Fehler ignorieren**  
 Der Fehler oder die Kürzung wird ignoriert, und die Datenzeile wird an die Ausgabe der CDC-Quelle umgeleitet.  
  
 **Zeile umleiten**  
 Der Fehler oder die Kürzung wird an die Fehlerausgabe der CDC-Quelle umgeleitet. In diesem Fall wird die Fehlerbehandlung der CDC-Quelle verwendet. Weitere Informationen finden Sie unter [CDC Source](data-flow/cdc-source.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Quellen-Editor für CDC &#40;Seite „Verbindungs-Manager“&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md)   
 [Quellen-Editor für CDC &#40;Seite „Spalten“&#41;](../../2014/integration-services/cdc-source-editor-columns-page.md)  
  
  
