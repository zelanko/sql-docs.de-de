---
title: Transformations-Editor für das Exportieren von Spalten (Seite Spalten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileextractortransformation.columns.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: b659a5c2-5509-4b5b-9c82-136c971d5c7f
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 2460e3a86c83dbd6b206bf173ac2c2691ecee685
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966730"
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
 Geben Sie an, ob Daten durch die Transformation an vorhandene Dateien angefügt werden sollen. Der Standardwert lautet `false`.  
  
 **Abschneiden erzwingen**  
 Geben Sie an, ob die Inhalte vorhandener Dateien vor dem Schreiben der Daten durch die Transformation gelöscht werden sollen. Der Standardwert lautet `false`.  
  
 **Bytereihenfolge-Marke schreiben**  
 Geben Sie an, ob eine Bytereihenfolge-Marke in die Datei geschrieben werden soll. Eine Bytereihenfolge-Marke wird nur geschrieben, wenn die Daten den Datentyp `DT_NTEXT` oder DT_WSTR aufweisen und nicht an eine vorhandene Datendatei angefügt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformations-Editor für das Exportieren von Spalten &#40;Seite „Fehlerausgabe“&#41;](../../2014/integration-services/export-column-transformation-editor-error-output-page.md)  
  
  
