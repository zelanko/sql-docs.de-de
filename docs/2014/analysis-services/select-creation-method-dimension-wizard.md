---
title: Erstellungs Methode auswählen (Dimensions-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensiondefinition.f1
ms.assetid: 291b0b2d-a03a-4df6-82f7-90ad92d4d1cf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6cc05e073bdb57033e4e618eb85a9c04fda76f5d
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84538213"
---
# <a name="select-creation-method-dimension-wizard"></a>Erstellungsmethode auswählen (Dimensions-Assistent)
  Auf der Seite **Erstellungsmethode auswählen** können Sie auswählen, wie die Dimension erstellt wird.  
  
 **So öffnen Sie den Dimensions-Assistenten**  
  
-   Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]im **Projektmappen-Explorer**mit der rechten Maustaste auf den Ordner **Dimensionen** eines [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekts, und klicken Sie anschließend auf **Neue Dimension**.  
  
## <a name="options"></a>Optionen  
 **Vorhandene Tabelle verwenden**  
 Erstellen Sie aus einer oder mehreren Tabellen einer Datenquelle eine Dimension. Welche Attribute für die Dimension verfügbar sind, hängt von der Struktur der in der Tabelle enthaltenen Daten ab.  
  
 Weitere Informationen finden Sie unter [Erstellen einer Dimension anhand einer vorhandenen Tabelle](multidimensional-models/create-a-dimension-by-using-an-existing-table.md).  
  
 **Zeittabelle in der Datenquelle generieren**  
 Erstellen Sie eine Zeittabelle in der zugrunde liegenden Datenquelle, und verwenden Sie diese Tabelle dann zum Erstellen einer Zeitdimension. Verwenden Sie diese Option, wenn keine solche Tabelle vorhanden ist und Sie sie nicht mithilfe eines Skripts erstellen möchten. Die neue Zeittabelle enthält Daten für den Datumsbereich, die Attribute und Kalender, die Sie im Assistenten angeben.  
  
> [!NOTE]  
>  Um diese Option nutzen zu können, müssen Sie über die Berechtigung zum Erstellen von Objekten in der zugrunde liegenden Datenquelle verfügen. Wenn Sie nicht zum Erstellen von Objekten in der Datenquelle berechtigt sind, verwenden Sie stattdessen die Option **Zeittabelle auf dem Server generieren** .  
  
 Weitere Informationen finden Sie unter [Erstellen einer Zeitdimension durch Generieren einer Zeittabelle](multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md).  
  
 **Zeittabelle auf dem Server generieren**  
 Erstellen Sie direkt auf dem Server eine Zeittabelle, und verwenden Sie diese Tabelle dann zum Erstellen einer Zeitdimension. Verwenden Sie diese Option, wenn Sie nicht über die Berechtigung zum Erstellen von Objekten in der zugrunde liegenden Datenquelle verfügen. Die neue Zeitdimension enthält Daten für den Datumsbereich, die Attribute und Kalender, die Sie im Assistenten angeben.  
  
 Weitere Informationen finden Sie unter [Erstellen einer Zeitdimension durch Generieren einer Zeittabelle](multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md).  
  
 **Nichtzeittabelle in der Datenquelle generieren**  
 Entwerfen Sie die Dimension ohne die zugrunde liegende relationale Datenquelle, und generieren Sie dann das notwendige Schema für die Datenquelle. Dieser Ansatz wird als Top-Down-Entwurf bezeichnet.  
  
> [!NOTE]  
>  Um diese Option nutzen zu können, müssen Sie über die Berechtigung zum Erstellen von Objekten in der zugrunde liegenden Datenquelle verfügen.  
  
 Sie können die Dimension mit oder ohne Vorlage erstellen. Um die Dimension mit einer Vorlage zu erstellen, wählen Sie die Vorlage in der Liste **Vorlage** aus.  
  
 Weitere Informationen finden Sie unter [Erstellen einer Dimension durch Generieren einer Nichtzeittabelle in der Datenquelle](multidimensional-models/create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md).  
  
 **Vorlage**  
 Wählen Sie die Vorlage aus, die Sie zum erstellen der Dimension verwenden möchten. Vorlagen stellen einen vollständigen Satz von Attributen und Hierarchiedefinitionen zur Verfügung, die einem bestimmten geschäftlichen Zweck dienen.  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn die Option **Nichtzeittabelle in der Datenquelle generieren** ausgewählt wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensions-Assistent F1-Hilfe](dimension-wizard-f1-help.md)   
 [Dimensionen &#40;Analysis Services Mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensionen in mehrdimensionalen Modellen](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
