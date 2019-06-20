---
title: Kompatibilitätsgrad für tabellarische Modelle in Analysis Services | Microsoft-Dokumentation
ms.date: 06/10/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 19c69aa1a1ab27e7498d3c9d6a0d52c25b9f0020
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66826832"
---
# <a name="compatibility-level-for-analysis-services-tabular-models"></a>Kompatibilitätsgrad für tabellarische Modelle von Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  Die *Kompatibilitätsgrad* bezieht sich auf Funktionen und Features, Verbesserungen in der Analysis Services-Engine und in den Metadaten für tabellarische Modelle. Im Allgemeinen sollten Sie die neuesten Kompatibilitätsgrad, die von Ihren Servern unterstützt auswählen. 

  **Die neueste unterstützte Kompatibilitätsgrad ist 1400** 
  
Wichtige Features in den Kompatibilitätsgrad 1400 sind:

*  Neue Infrastruktur für die Datenkonnektivität und den Import in tabellarische Modelle mit Unterstützung für TOM-APIs und TMSL-Skripts. Dies ermöglicht die Unterstützung für zusätzliche Datenquellen, z.B. Azure Blob Storage. Zusätzliche Daten, die Quellen werden werden in zukünftigen Updates enthalten.
*  Datentransformations- und datenmashupfunktionen mithilfe von Get Data- und M-Ausdrücken in SQL Server Data Tools (SSDT).
*  Misst nun Unterstützung für eine detailzeileneigenschaft mit einem DAX-Ausdruck, aktivieren die BI-tools wie z. B. Microsoft Excel einen Drilldown nach unten zu Daten aus einem aggregierten Bericht beschrieben. Wenn Benutzer den Gesamtumsatz für eine Region und Monat anzeigen, können sie z. B. die zugehörigen Auftragsdetails anzeigen. 
*  Sicherheit der auf Objektebene für Tabellen- und Spaltennamen, zusätzlich zu den darin enthaltenen Daten.
*  Verbesserte Unterstützung für unregelmäßige Hierarchien.
*  Überwachung von Leistung und Verbesserungen.

  
## <a name="supported-compatibility-levels-by-version"></a>Unterstützte Kompatibilitätsgrade nach version
  
Niedrigere Kompatibilitätsgraden werden Gründen der Abwärtskompatibilität unterstützt Kompatibilität. 

|||  
|-|-|- 
|**Kompatibilitätsgrad**|**Serverversion**| 
|1470|SQL Server-2019 (CTP 2.3 und höher) | 
|1400|Azure Analysis Services, SqlServer 2019, SqlServer 2017 |  
|1200|Azure Analysis Services, SqlServer 2019, SqlServer 2017 SQLServer 2016| 
|1103|SQLServer 2017 *, SqlServer 2016, SqlServer 2014, SQL Server 2012 SP1|  
|1100|SQLServer 2017 *, SqlServer 2016, SqlServer 2014, SQL Server 2012 SP1, SqlServer 2012| 

\* Kompatibilitätsgrad von 1100 und 1103 sind in SQL Server 2017 und höher veraltet.
  
## <a name="set-compatibility-level"></a>Festlegen des Kompatibilitätsgrads 
 Beim Erstellen eines neuen tabellenmodellprojekts in SQL Server Data Tools (SSDT) können Sie den Kompatibilitätsgrad angeben, auf die **Designer für tabellarische Modelle** Dialogfeld. 
  
 ![ssas_tabularproject_compat1200](../../analysis-services/tabular-models/media/ssas-tabularproject-compat1200.png)  
  
 Bei Auswahl der **diese Meldung nicht mehr anzeigen** auswählen, werden allen nachfolgenden Projekten der als Standard angegebene Kompatibilitätsgrad verwendet. Sie können den Standardkompatibilitätsgrad in SSDT unter **Tools** > **Optionen**ändern.  
  
 Zum Upgraden eines tabellenmodellprojekts in SSDT legen die **Kompatibilitätsgrad** Eigenschaft im Modell **Eigenschaften** Fenster. Beachten Sie, Aktualisieren des Kompatibilitätsgrads nicht rückgängig gemacht werden.
  
## <a name="check-compatibility-level-for-a-database-in-ssms"></a>Überprüfen des Kompatibilitätsgrads einer Datenbank in SSMS  
 In SSMS mit der Maustaste des Datenbanknamens > **Eigenschaften** > **Kompatibilitätsgrad**.  
  
## <a name="check-supported-compatibility-level-for-a-server-in-ssms"></a>Überprüfen des unterstützten Kompatibilitätsgrads für einen Server in SSMS  
 Klicken Sie in SSMS mit der rechten Maustaste auf den Servernamen > **Eigenschaften** > **Unterstützter Kompatibilitätsgrad**.  

 Diese Eigenschaft gibt den höchsten Kompatibilitätsgrad einer Datenbank, die auf dem Server ausgeführt wird. Der unterstützte Kompatibilitätsgrad ist schreibgeschützt und kann nicht geändert werden.
 
> [!NOTE]  
>  In SSMS wird beim Verbinden mit einer SQL Server Analysis Services-Server, Azure Analysis Services-Server oder Power BI Premium-Arbeitsbereich die Eigenschaft unterstützter Kompatibilitätsgrad 1200 angezeigt. Dies ist ein bekanntes Problem und wird in einem zukünftigen SSMS aufgelöst aktualisieren. Wenn aufgelöst, wird diese Eigenschaft die höchsten unterstützte Kompatibilitätsgrad angezeigt. 
  
## <a name="see-also"></a>Siehe auch  
 [Kompatibilitätsgrad einer mehrdimensionalen Datenbank](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [What's new in Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Erstellen eines neuen tabellarischen modellprojekts](../../analysis-services/tabular-models/create-a-new-tabular-model-project-analysis-services.md)  
  
  
