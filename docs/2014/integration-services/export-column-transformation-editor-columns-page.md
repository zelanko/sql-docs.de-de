---
title: Exportieren Sie die Spalte mit der Transformations-Editor (Spaltenseite) | Microsoft-Dokumentation
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
- sql12.dts.designer.fileextractortransformation.columns.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: b659a5c2-5509-4b5b-9c82-136c971d5c7f
caps.latest.revision: 28
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b427d8a727f0db31b63d43efbe00378c7ef0f18b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37207450"
---
# <a name="export-column-transformation-editor-columns-page"></a>Transformations-Editor für das Exportieren von Spalten (Seite Spalten)
  Auf der Seite **Spalten** des Dialogfelds **Transformations-Editor für das Exportieren von Spalten** können Sie die Spalten im Datenfluss angeben, die in Dateien extrahiert werden sollen. Sie können angeben, ob die Daten durch die Transformation für das Exportieren von Spalten an eine Datei angefügt werden, oder ob eine vorhandene Datei mit den Daten überschrieben wird.  
  
 Weitere Informationen zur Transformation für das Exportieren von Spalten finden Sie unter [Export Column Transformation](data-flow/transformations/export-column-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Spalte extrahieren**  
 Wählen Sie Spalten aus der Liste der Eingabespalten aus, die Text- oder Bilddaten enthalten. Alle Zeilen sollten Definitionen für **Spalte extrahieren** und **Dateipfadspalte**aufweisen.  
  
 **Dateipfadspalte**  
 Wählen Sie Spalten aus der Liste der Eingabespalten aus, die Dateipfade und Dateinamen enthalten. Alle Zeilen sollten Definitionen für **Spalte extrahieren** und **Dateipfadspalte**aufweisen.  
  
 **Anfügen zulassen**  
 Geben Sie an, ob Daten durch die Transformation an vorhandene Dateien angefügt werden sollen. Der Standardwert ist `false`.  
  
 **Abschneiden erzwingen**  
 Geben Sie an, ob die Inhalte vorhandener Dateien vor dem Schreiben der Daten durch die Transformation gelöscht werden sollen. Der Standardwert ist `false`.  
  
 **Bytereihenfolge-Marke schreiben**  
 Geben Sie an, ob eine Bytereihenfolge-Marke in die Datei geschrieben werden soll. Eine BOM wird nur geschrieben, wenn die Daten der `DT_NTEXT` oder DT_WSTR-Datentyp ist, und nicht an eine vorhandene Datendatei angefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Exportieren der Transformations-Editor Spalten &#40;Seite "Fehlerausgabe"&#41;](../../2014/integration-services/export-column-transformation-editor-error-output-page.md)  
  
  
