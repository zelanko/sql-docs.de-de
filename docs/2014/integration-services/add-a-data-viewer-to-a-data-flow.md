---
title: Hinzufügen eines Daten-Viewers zu einem Datenfluss | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data viewers [Integration Services]
- data flow [Integration Services], data viewers
- adding data viewers
ms.assetid: 5e573274-a170-4132-bfc8-a8ff3a8411e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e04e678dfb2b98e5304f9f7c9f0cfe2a858b6485
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439767"
---
# <a name="add-a-data-viewer-to-a-data-flow"></a>Hinzufügen eines Daten-Viewers zu einem Datenfluss
  In diesem Thema wird beschrieben, wie ein Daten-Viewer in einem Datenfluss hinzugefügt und konfiguriert wird. Ein Daten-Viewer zeigt Daten an, die sich zwischen zwei Datenflusskomponenten bewegen. Ein Daten-Viewer kann z. B. die Daten anzeigen, die von einer Datenquelle extrahiert werden, bevor die Daten von einer Transformation im Datenfluss geändert werden.  
  
 Ein Pfad verbindet Komponenten in einem Datenfluss, indem die Ausgabe einer Datenflusskomponente mit der Eingabe einer anderen Komponente verbunden wird.  
  
 Bevor Sie einem Paket Daten-Viewer hinzufügen können, muss das Paket einen Datenfluss-Task enthalten und mindestens zwei verbundene Datenflusskomponenten.  
  
### <a name="to-add-a-data-viewer-to-a-data-flow"></a>So fügen Sie einem Datenfluss einen Daten-Viewer hinzu  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** , falls sie nicht bereits aktiviert ist.  
  
4.  Klicken Sie auf den Datenflusstask, an dessen Datenfluss Sie einen Daten-Viewer anfügen möchten, und klicken Sie dann auf die Registerkarte **Datenfluss** .  
  
5.  Klicken Sie mit der rechten Maustaste auf einen Pfad zwischen zwei Datenflusskomponenten, und klicken Sie auf **Bearbeiten**.  
  
6.  Auf der Seite **Allgemein** können Sie Pfadeigenschaften anzeigen und bearbeiten. Beispielsweise können Sie aus der Dropdownliste **PathAnnotation** die Anmerkung auswählen, die neben dem Pfad angezeigt wird.  
  
7.  Auf der Seite **Metadaten** können Sie die Spaltenmetadaten anzeigen und die Metadaten in die Zwischenablage kopieren.  
  
8.  Klicken Sie auf der Seite **Daten-Viewer** auf **Daten-Viewer aktivieren**.  
  
9. Wählen Sie im Bereich Anzuzeigende Spalten die Spalten aus, die im Daten-Viewer angezeigt werden sollen. Standardmäßig werden alle verfügbaren Spalten ausgewählt und in der Liste **Angezeigte Spalten** aufgeführt. Verschieben Sie Spalten, die Sie nicht verwenden möchten, in die Liste **Nicht verwendete Spalten** , indem Sie diese auswählen und dann auf den linken Pfeil klicken.  
  
    > [!NOTE]  
    >  Im Raster werden Werte, die die Datentypen DT_DATE, DT_DBTIME2, DT_FILETIME, DT_DBTIMESTAMP, DT_DBTIMESTAMP2 und DT_DBTIMESTAMPOFFSET darstellen, als ISO 8601-formatierte Zeichenfolgen angezeigt, und das `T`-Trennzeichen wird durch ein Leerzeichen ersetzt. Werte, die den DT_DATE-Datentyp und den DT_FILETIME-Datentyp darstellen, enthalten sieben Ziffern für Sekundenbruchteile. Da der DT_FILETIME-Datentyp nur drei Ziffern von Sekundenbruchteilen speichert, zeigt das Raster Nullen für die restlichen vier Ziffern an. Werte, die den DT_DBTIMESTAMP-Datentyp darstellen, enthalten drei Ziffern für Sekundenbruchteile. Für Werte, die die Datentypen DT_DBTIME2, DT_DBTIMESTAMP2 und DT_DBTIMESTAMPOFFSET darstellen, entspricht die Anzahl der Ziffern für Sekundenbruchteile der für den Datentyp der Spalte festgelegten Skala. Weitere Informationen zu ISO 8601-Formaten finden Sie unter [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md). Weitere Informationen zu Datentypen finden Sie unter [Integration Services Data Types](data-flow/integration-services-data-types.md).  
  
10. Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services Transformationen](data-flow/transformations/integration-services-transformations.md)   
 [Integration Services Pfade](data-flow/integration-services-paths.md)   
 [Datenfluss](data-flow/data-flow.md)   
 [Debuggen des Datenflusses](troubleshooting/debugging-data-flow.md)  
  
  
