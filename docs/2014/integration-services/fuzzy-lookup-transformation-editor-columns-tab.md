---
title: Fuzzy Lookup Transformations-Editor (Registerkarte Spalten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.columns.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: aaf45327-79e9-4760-9b4d-546ace91b5b4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 063248c6b91aebf6198323487aa30ddd1c9cb6ec
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66058332"
---
# <a name="fuzzy-lookup-transformation-editor-columns-tab"></a>Transformations-Editor für Fuzzysuche (Registerkarte Spalten)
  Auf der Registerkarte **Spalten** des Dialogfelds **Transformations-Editor für Fuzzysuche** können Sie die Eigenschaften für die Eingabe- und Ausgabespalten festlegen.  
  
 Weitere Informationen zur Transformation für Fuzzysuche finden Sie unter [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Optionen  
 **Verfügbare Eingabespalten**  
 Um Eingabespalten mit verfügbaren Suchspalten zu verbinden, ziehen Sie diese auf die Suchspalten. Diese Spalten müssen übereinstimmende, unterstützte Datentypen aufweisen. Wählen Sie eine Zuordnungszeile aus, und klicken Sie mit der rechten Maustaste darauf, um die Zuordnungen im Dialogfeld [Beziehungen erstellen](data-flow/transformations/create-relationships.md) zu bearbeiten.  
  
 **Name**  
 Zeigen Sie die Namen der verfügbaren Eingabespalten an.  
  
 **Pass-Through**  
 Geben Sie an, ob die Eingabespalten in der Ausgabe der Transformation eingeschlossen sein sollen.  
  
 **Verfügbare Suchspalten**  
 Wählen Sie mithilfe der Kontrollkästchen die Spalten aus, für die die Fuzzysuchvorgänge ausgeführt werden sollen.  
  
 **Suchspalte**  
 Wählen Sie Suchspalten aus der Liste der verfügbaren Spalten der Verweistabelle aus. Ihre Auswahl wird entsprechend in der Auswahl der Kontrollkästchen in der **Verfügbare Suchspalten** -Tabelle deutlich. Durch das Auswählen einer Spalte in der **Verfügbare Suchspalten** -Tabelle wird eine Ausgabespalte erstellt, die den Spaltenwert der Verweistabelle für jede übereinstimmende Zeile enthält, die zurückgegeben wird.  
  
 **Ausgabealias**  
 Geben Sie einen Alias für die Ausgabe der einzelnen Suchspalten ein. Standardmäßig wird der Name der Suchspalte mit einem angefügten numerischen Indexwert verwendet. Sie können jedoch auch einen beschreibenden Namen angeben, sofern dieser eindeutig ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformations-Editor für Fuzzysuche &#40;Registerkarte „Verweistabelle“&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [Transformations-Editor für Fuzzysuche &#40;Registerkarte „Erweitert“&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  
