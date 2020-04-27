---
title: Farb Regeln für Karten (Dialog Feld), allgemein | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10541"
- sql12.rtp.rptdesigner.shared.mapcolorrulesgeneral.f1
ms.assetid: 14ff5fc1-4cf8-4a45-9d98-47a1bf1c52c4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e97de85cdd57fdb21aa82379243eb6954358ea38
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108321"
---
# <a name="map-color-rules-dialog-box-general"></a>Farbregeln der Karte (Dialogfeld), Allgemein
  Wählen Sie **Allgemein** im Dialogfeld für Farbregeleigenschaften **** aus, um Farboptionen für Kartenelemente in dieser Ebene zu definieren. Kartenelemente sind Polygone, Linien und Punkte. Farbregeln können angewendet werden, wenn Sie auf der Grundlage räumlicher Daten und analytischer Daten in einem Datasetfeld oder in einem räumlichen Datenquellenfeld eine Beziehung zwischen Kartenelementen erstellt haben.  
  
 Um alle Kartenelemente einer Ebene durch Angeben eines dekorativen Farbverlaufs mit unterschiedlichen primären und sekundären Farben anzuzeigen, verwenden Sie im Dialogfeld Polygoneigenschaften von Karten die Seite **Ausfüllen** . Farbregeln haben Vorrang gegenüber Anzeigeeigenschaften für eine Ebene. Weitere Informationen finden Sie unter [Anpassen der Daten und der Anzeige einer Karte oder einer Kartenebene &#40;Berichts-Generator und SSRS&#41;](report-design/customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Optionen  
 **Vorlagenstil anwenden**  
 Aktivieren Sie diese Option, um Farbe auf Grundlage des Designs zu verwenden, das im Assistenten ausgewählt wurde oder in den Polygon-, Linien- oder Punktebeneneigenschaften festgelegt wurde. Ein Design legt Standardoptionen für Farbe, Schriftart und Rahmen für die Karte fest. Für diese Option wird keine Regel angewendet, um Farben jedem Kartenelement zuzuweisen.  
  
 **Daten mithilfe der Farbpalette anzeigen**  
 Aktivieren Sie diese Option, um analytische Daten mithilfe von Farben aus einer bestimmten Farbpalette visuell darzustellen.  
  
 **Daten mithilfe von Farbbereichen anzeigen**  
 Aktivieren Sie diese Option, um analytische Daten mit einem Bereich von Farben für jedes Kartenelement visuell darzustellen. Wenn Sie z. B. Rot als Startfarbe, Gelb als mittlere Farbe und Grün als Endfarbe angeben, sind Werte im niedrigen Bereich rot, Werte im mittleren Bereich sind gelb, und Werte im obersten Bereich sind grün.  
  
 **Daten mithilfe benutzerdefinierter Farben anzeigen**  
 Aktivieren Sie diese Option, um analytische Daten durch das Angeben einer eigenen Liste von Farben visuell darzustellen.  
  
 **Datenfeld**  
 Diese Option wird angezeigt, wenn Sie eine der Optionen **Daten anzeigen** auswählen.  
  
 Wählen Sie in der Dropdownliste das zu verwendende Feld mit analytischen Daten aus. Abhängig von der Quelle räumlicher Daten zeigt die Liste Felder aus der räumlichen Datenquelle an und aus einem Berichtsdataset, das eine Beziehung zwischen den räumlichen Daten und analytischen Daten darstellt. Um eine solche Beziehung zu erstellen, legen Sie auf der Seite "Analytische Daten" für die ausgewählte Kartenebene die Datenoptionen fest.  
  
 **Messer**  
 Geben Sie den Namen der Farbpalette ein, oder wählen Sie ihn aus.  
  
 **Startfarbe**  
 Geben Sie die Farbe an, die für Daten am niedrigen Ende des Datenbereichs verwendet werden soll.  
  
 **Mittelfarbe**  
 Geben Sie die Farbe an, die für Daten in der Mitte des Datenbereichs verwendet werden soll. Wählen Sie **Keine Farbe** aus, um diesen Bereich zu entfernen.  
  
 **Endfarbe**  
 Geben Sie die Farbe an, die für Daten am oberen Ende des Datenbereichs verwendet werden soll.  
  
 **Add (Hinzufügen)**  
 Klicken Sie auf **Hinzufügen** , um eigene Farben für die Farbregel anzugeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Karten &#40;Berichts-Generator und SSRS&#41;](report-design/maps-report-builder-and-ssrs.md)   
 [Ändern der Kartenlegenden, Farbskala und zugeordneten Regeln &#40;Berichts-Generator und SSRS&#41;](report-design/change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md)  
  
  
