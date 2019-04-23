---
title: 'rrRenderingError: Reporting Services-Fehler | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rrRenderingError
ms.assetid: 0751efc3-b81b-44ee-8aac-8560f86ca322
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 48a9f4428dfc2457e06dc667837d3bde09c7380d
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59933667"
---
# <a name="rrrenderingerror---reporting-services-error"></a>rrRenderingError – Reporting Services-Fehler
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|rrRenderingError|  
|Ereignisquelle|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources.Strings|  
|Komponente|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Meldungstext|Fehler beim Rendern des Berichts. (rrRenderingError) %1|  
  
## <a name="explanation"></a>Erklärung  
 Diese Meldung wird zurückgegeben, wenn der Bericht von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nicht gerendert oder exportiert werden kann.  
  
 Eine Meldung, in der angegeben wird, dass das Format nicht unterstützt wird, ist normalerweise darauf zurückzuführen, dass das angegebene RDL-Seitenformat nicht gültig ist. Geben Sie ein gültiges RDL-Seitenformat an, und versuchen Sie es dann erneut.  
  
 Eine Meldung, in der angegeben wird, dass ein RDL-Formatmaß nicht unterstützt wird, ist normalerweise darauf zurückzuführen, dass ein nicht unterstützter Einheitentyp angegeben wurde. Gültige Einheitentypen sind cm, in, mm, pc und pt. Geben Sie einen gültigen Einheitentyp an, und versuchen Sie es dann erneut.  
  
 Eine Meldung, in der angegeben wird, dass ein negatives Format nicht unterstützt wird, ist normalerweise darauf zurückzuführen, dass für das Seitenformat ein negatives Maß angegeben wurde. Geben Sie eine positive Zahl für das Seitenformat an, und versuchen Sie es dann erneut.  
  
 Eine Meldung, in der angegeben wird, dass ein RDL-Format außerhalb des zulässigen Bereichs angegeben wurde, ist normalerweise darauf zurückzuführen, dass ein Maß des Papierformats außerhalb des zulässigen Seitenrandformats liegt. Geben Sie ein Maß für das Seitenformat an, das innerhalb der gültigen Seitenrandformate liegt.  
  
 Eine Meldung, in der angegeben wird, dass eine angegebene Farbe nicht unterstützt wird, ist normalerweise darauf zurückzuführen, dass eine in der RDL angegebene Farbe nicht gültig ist. Wählen Sie eine von RDL unterstützte Farbe aus, und versuchen Sie es dann erneut.  
  
 Eine Meldung, in der angegeben wird, dass die Aktionsbezeichnung nur optional ist, wenn nur eine einzelne Aktion verwendet wird, und dass das Hinzufügen von mehreren Aktionen Bezeichnungen für die einzelnen Aktionen erfordert, ist normalerweise darauf zurückzuführen, dass zwar eine Aktionsbezeichnung angegeben wurde, diese aber ungültig ist. Geben Sie eine gültige Aktionsbezeichnung für jede Aktion an.  
  
 Eine Meldung, in der angegeben wird, dass ein Stilargument von einem bestimmten Typ sein muss, ist normalerweise darauf zurückzuführen, dass ein ungültiger Stilwert für den Datentyp angegeben wurde. Die RDL-Spezifikation identifiziert die gültigen Typen, die Sie in den Stilwerten der verschiedenen RDL-Elemente verwenden können. Beispielsweise ist ein falscher Stilwert für die Hintergrundfarbe "2pt" und ein falscher Wert für die Höhe "true". Geben Sie einen richtigen Wert an, und versuchen Sie es dann erneut.  
  
 Eine Meldung, in der angegeben wird, dass eine Rahmenart nicht unterstützt wird, ist normalerweise darauf zurückzuführen, dass eine angegebene Rahmenart nicht gültig ist. Geben Sie eine unterstützte Rahmenart an, und versuchen Sie es dann erneut.  
  
 Eine Meldung, in der angegeben wird, dass der Bild-Mimetyp nicht unterstützt wird, ist normalerweise darauf zurückzuführen, dass der für ein Bildberichtselement angegebene Mimetyp nicht gültig ist. Geben Sie einen unterstützten Mimetyp für das Berichtselement an, und versuchen Sie es dann erneut.  
  
 Eine Meldung, in der angegeben wird, dass die Zeilenanzahl die maximal pro Blatt zulässigen Zeilen übersteigt, ist normalerweise darauf zurückzuführen, dass die Zeilenanzahl eines Excel-Arbeitsblatts überschritten wurde. Excel unterstützt bis zu 65.000 Zeilen.  
  
 Eine Meldung, in der angegeben wird, dass die Spaltenanzahl die maximal pro Blatt zulässigen Spalten übersteigt, ist normalerweise darauf zurückzuführen, dass die Spaltenanzahl eines Excel-Arbeitsblatts überschritten wurde.  
  
## <a name="user-action"></a>Benutzeraktion  
  
## <a name="internal-only"></a>Nur intern  
  
