---
title: Benutzerdefinierte Karten in mobilen Reporting Services-Berichten | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über geografische Karten im Publisher für mobile Berichte von Microsoft SQL Server, die im Format für ESRI-Shape-Dateien definiert werden.
ms.date: 12/06/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 59a4ebad-587a-4770-afcd-c69216b8afd9
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 17975defea6029e4077acbe45fd3f8b0d7495267
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53212079"
---
# <a name="custom-maps-in-reporting-services-mobile-reports"></a>Benutzerdefinierte Karten in mobilen Reporting Services-Berichten
Geografische Karten werden im Publisher für mobile Berichte von Microsoft SQL Server in dem Format *Shapefile* von ESRI definiert.  
  
Dieses wurde ursprünglich von einem privaten Unternehmen entwickelt und ist inzwischen ein weitverbreitetes halboffenes Format, das in vielen Geoinformationssystem-Anwendungen verwendet wird. Diesem Format entsprechend erfordert der Publisher für mobile Berichte, dass beim Definieren einer Karte zwei Dateien bereitgestellt werden:  
  
- Eine SHP-Datei für Shapegeometrien  
- Eine DBF-Datei für Metadaten  
  
Die Basisdateinamen müssen übereinstimmen (z. B. *canada.shp* und *canada.dbf*). Die Metadaten müssen das Feld *NAME* mit dem Namen (Schlüssel) der entsprechenden Shape enthalten, die beim Auffüllen der Karte mit Daten verwendet werden soll.  

Die beiden Kartendateien (die SHP-Datei und die DBF-Datei) dürfen zusammen nicht größer als 512 KB sein. Wenn die Kartendateien zu groß sind, verkleinern Sie sie mit einem Tool, z.B. [https://mapshaper.org/](https://mapshaper.org/).  
  
Erfahren Sie, wie Sie [mobilen Berichten benutzerdefinierte Karten hinzufügen](../../reporting-services/mobile-reports/add-a-custom-map-to-a-reporting-services-mobile-report.md).  
  
## <a name="technical-information"></a>Technische Informationen  
  
- Offizielle Spezifikation: [https://www.esri.com/library/whitepapers/pdfs/shapefile.pdf](https://www.esri.com/library/whitepapers/pdfs/shapefile.pdf)  
- Wikipedia-Shape-Datei-Artikel: [https://en.wikipedia.org/wiki/Shapefile](https://en.wikipedia.org/wiki/Shapefile)  
  
## <a name="creating--editing-map-geometry"></a>Erstellen und Bearbeiten der Kartengeometrie  
  
Das Erstellen und Bearbeiten von Shape-Dateien ist ein komplexer Prozess, dessen Erläuterung den Rahmen dieses Dokuments sprengen würde. Sie können für die ersten Schritte die folgenden Ressourcen und Anwendungen verwenden:  
  
- ArcGIS: [https://www.arcgis.com/](https://www.arcgis.com/)  
- MAPublisher-Plug-In für Adobe Illustrator: [https://www.avenza.com/mapublisher](https://www.avenza.com/mapublisher)  
- QuantumGIS (kostenlos): [https://www.qgis.org/](https://www.qgis.org/)  

## <a name="existing-shapefiles"></a>Vorhandene Shape-Dateien  
  
Aus dem Internet können viele vorhandene Shape-Dateien heruntergeladen werden, z. B. von Websites wie Diva-GIS ([https://www.diva-gis.org/Data](https://www.diva-gis.org/Data)).  

## <a name="see-also"></a>Siehe auch  
- [Karten in mobilen Reporting Services-Berichten](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [Erstellen und Veröffentlichen von mobilen Berichten mit dem Publisher für mobile Berichte von SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
