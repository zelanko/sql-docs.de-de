---
title: Transformation Editor für Ausdruckssuche (Registerkarte "Ausdruckssuche" Term) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookup.termlookup.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
caps.latest.revision: 25
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b5d09acf4a96b0380e9c6c587044bf9d5bede55c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227730"
---
# <a name="term-lookup-transformation-editor-term-lookup-tab"></a>Transformations-Editor für Ausdruckssuche (Registerkarte Ausdruckssuche)
  Mithilfe der Registerkarte **Ausdruckssuche** des Dialogfelds **Transformations-Editor für Ausdruckssuche** können Sie eine Eingabespalte einer Suchspalte in einer Verweistabelle zuordnen und einen Alias für jede Ausgabespalte bereitstellen.  
  
 Weitere Informationen zur Transformation für Ausdruckssuche finden Sie unter [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Verfügbare Eingabespalten**  
 Wählen Sie mithilfe der Kontrollkästchen die Eingabespalten aus, die unverändert an die Ausgabe weitergegeben werden. Ziehen Sie eine Eingabespalte auf die Liste **Verfügbare Verweisspalten** , um sie einer Suchspalte in der Verweistabelle zuzuordnen. Die Eingabe- und Suchspalten müssen übereinstimmende, unterstützte Datentypen haben, entweder DT_NTEXT oder DT_WSTR. Wählen Sie eine Zuordnungszeile aus, und klicken Sie mit der rechten Maustaste darauf, um die Zuordnungen im Dialogfeld [Beziehungen erstellen](data-flow/transformations/create-relationships.md) zu bearbeiten.  
  
 **Verfügbare Verweisspalten**  
 Zeigen Sie die verfügbaren Spalten in der Verweistabelle an. Wählen Sie die Spalte aus, die die Liste der Ausdrücke enthält, für die nach einer Übereinstimmung gesucht wird.  
  
 **Pass-Through-Spalte**  
 Wählen Sie Spalten aus der Liste der verfügbaren Eingabespalten aus. Ihre Auswahl wird entsprechend in der Auswahl der Kontrollkästchen in der **Verfügbare Eingabespalten** -Tabelle deutlich.  
  
 **Alias der Ausgabespalte**  
 Geben Sie einen Alias für jede Spalte ein. Standardmäßig wird der Name der Spalte verwendet. Sie können jedoch auch einen beschreibenden Namen angeben, sofern dieser eindeutig ist.  
  
 **Konfigurieren der Fehlerausgabe**  
 Geben Sie mit dem Dialogfeld [Fehlerausgabe konfigurieren](../../2014/integration-services/configure-error-output.md) die Optionen zur Fehlerbehandlung für Zeilen an, die Fehler verursachen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformations-Editor Begriff &#40;verweisen auf die Registerkarte "Tabelle"&#41;](../../2014/integration-services/term-lookup-transformation-editor-reference-table-tab.md)   
 [Transformations-Editor Begriff &#40;Registerkarte "Erweitert"&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md)   
 [Transformation für Ausdrucksextrahierung](data-flow/transformations/term-extraction-transformation.md)  
  
  
