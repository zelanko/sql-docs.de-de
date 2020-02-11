---
title: Eigenschaften des Kartenviewports (Dialog Feld), allgemein | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.general.f1
- "10505"
ms.assetid: 6c9c773e-5c56-4571-95ed-8a157cfdfe52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8ec0aaa051ba317cd05a9784c80fb997f5fa19e6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108236"
---
# <a name="map-viewport-properties-dialog-box-general"></a>Eigenschaften des Kartenviewports (Dialogfeld), Allgemein
  Wählen Sie im Dialogfeld **Viewporteigenschaften zuordnen** den Bereich **Allgemein** aus, um das Koordinatensystem, die Projektion und die Begrenzungsoptionen zu ändern.  
  
## <a name="options"></a>Tastatur  
 **Koordinatensystem**  
 Geben Sie den Typ des Koordinatensystems an, das für die Kartendaten verwendet wird.  
  
-   **Planar** Wählen Sie diese Option aus, wenn sich Kartendaten in X-und Y-Koordinaten befinden, z. b. zum Planen von Plänen.  
  
-   **Geografisch** Wählen Sie diese Option aus, wenn sich Kartendaten in Längen-und Breitengrad Koordinaten befinden, z. b. für Orte der Stadt.  
  
 **Projektion**  
 Geben Sie die Methode an, die verwendet werden soll, um geografische Koordinaten auf eine zweidimensionale Oberfläche zu projizieren. Wählen Sie eine Projektion aus, die mit den visuell darzustellenden Daten kompatibel ist. Die vier räumlichen Eigenschaften, die von der Projektion betroffen sind, sind Bereich, Form, Entfernung und Richtung. Bei Ansichten der Erde hängt eine gute Auswahl der Projektion von der Mittelpunktansicht, den Kartenbegrenzungen und dem Zoomfaktor ab.  
  
 Jede der folgenden Projektionen wahrt mindestens eine der folgenden räumlichen Eigenschaften:  
  
-   **Equirecht eckig** Wählen Sie diese Option aus, um Längen-und Breitengrad als rechteckige Koordinaten zu verwenden.  
  
-   **Mercator** Wählen Sie diese beliebte Projektion für kleinere Bereiche, für eine geringere Verzerrung um den Äquator oder wenn Sie eine Kartenebene mit einer vorhandenen Kachel Ebene hinzufügen möchten, die die Mercator-Projektion verwendet.  
  
-   **Robinson** Wählen Sie diese Option aus, um weniger große Bereiche, die sich vom Äquator bis zu den Polen erstrecken. Diese Projektion wurde von Arthur H. Robinson im Jahr 1963 entwickelt.  
  
-   **Fahey** Wählen Sie diese Option aus, um weniger große Bereiche, die sich vom Äquator bis zu den Polen erstrecken. Diese Projektion wurde von Lawrence Fahey im Jahr 1975 entwickelt.  
  
-   **Eckert1** Wählen Sie diese Option aus, um parallele Abstände in breiten-und geraden Linien für Meridiane im Längengrad zu verwenden.  
  
-   **Eckert3** Wählen Sie diese Option aus, um parallele Abstände im Breitengrad und gekrümmte Linien für Meridiane im Längengrad zu verwenden.  
  
-   **Hammeraium** Wählen Sie diese Option für Polar Maps oder World Maps aus.  
  
-   **Wagner3** Wählen Sie diese Option für Weltkarten aus.  
  
-   **Bonne** Wählen Sie diese Option aus, um die Welt anzuzeigen, wie Sie in einem Atlas angezeigt wird.  
  
 **Seitenumbruchoptionen**  
 Wählen Sie Optionen aus, um anzugeben, wie der Inhalt an eine Berichtsseite angepasst wird.  
  
 **Begrenzungsoptionen**  
 Geben Sie die Unter- und die Obergrenzen für Koordinaten an, um zu steuern, welcher Teil der Karte im Bericht angezeigt wird.  
  
 **Minimum (X)**  
 Niedrigster X-Wert. Nur für **Planar** verfügbar.  
  
 **Maximum (X)**  
 Höchster X-Wert. Nur für **Planar** verfügbar.  
  
 **Minimum (Y)**  
 Niedrigster Y-Wert. Nur für **Planar** verfügbar.  
  
 **Maximum (Y)**  
 Höchster Y-Wert. Nur für **Planar** verfügbar.  
  
 **Minimale Länge**  
 Niedrigster Längenwert. Nur für **Geografisch** verfügbar.  
  
 **Maximale Länge**  
 Höchster Längenwert. Nur für **Geografisch** verfügbar.  
  
 **Minimale Breite**  
 Niedrigster Breitenwert. Nur für **Geografisch** verfügbar.  
  
 **Maximale Breite**  
 Höchster Breitenwert. Nur für **Geografisch** verfügbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Karten &#40;Berichts-Generator und SSRS&#41;](report-design/maps-report-builder-and-ssrs.md)  
  
  
