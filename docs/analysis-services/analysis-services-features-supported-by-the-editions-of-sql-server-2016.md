---
title: Analysis Services-Funktionen, die von den Editionen von SQLServer unterstützte | Microsoft-Dokumentation
ms.date: 06/25/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9947b10e01864f66bf26d6599e43814ab37dadc6
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67388208"
---
# <a name="analysis-services-features-supported-by-sql-server-edition"></a>Analysis Services-Funktionen von SQL Server-Edition unterstützt werden
[!INCLUDE[ssas-appliesto-sql2016-later](../includes/ssas-appliesto-sql2016-later.md)]

Dieser Artikel beschreibt Funktionen, die von den verschiedenen Editionen von SQL Server 2016, 2017 2019 Analysis Services unterstützt werden. Evaluation-Edition unterstützt die Funktionen der Enterprise Edition.

## <a name="analysis-services-servers"></a>Analysis Services (Server)
  
|Funktion|Enterprise|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|Entwickler|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Skalierbare, freigegebene Datenbanken|Ja||||||Ja|  
|Sichern/Wiederherstellen und Anfügen/Trennen von Datenbanken|Ja|Ja|||||Ja|  
|Synchronisieren von Datenbanken|Ja||||||Ja|  
|Always On-Failoverclusterinstanzen|Ja<br /><br /> Anzahl der Knoten ist das Maximum des Betriebssystems|Ja<br /><br /> Unterstützung für 2 Knoten|||||Ja<br /><br /> Anzahl der Knoten ist das Maximum des Betriebssystems|  
|Programmierbarkeit (AMO, ADOMD.NET, OLEDB, XML/A, ASSL, TMSL)|Ja|Ja|||||Ja|  
  
## <a name="tabular-models"></a>Tabellarische Modelle 
  
|Funktion|Enterprise|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|Entwickler|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Hierarchien|Ja|Ja|||||Ja|  
|KPIs (Key Performance Indicators)|Ja|Ja|||||Ja|  
|Perspektiven|Ja||||||Ja|  
|Translations|Ja|Ja|||||Ja|  
|DAX-Berechnungen, DAX-Abfragen, MDX-Abfragen|Ja|Ja|||||Ja|  
|Sicherheit auf Zeilenebene|Ja|Ja|||||Ja|  
|Mehrere Partitionen|Ja||||||Ja|  
|Berechnungsgruppen|Ja (beginnend mit SQL Server-2019)|Ja (beginnend mit SQL Server-2019)|||||Ja (beginnend mit SQL Server-2019)|  
|InMemory-Speichermodus|Ja|Ja|||||Ja|  
|DirectQuery-Modus|Ja|Ja (beginnend mit SQL Server-2019)|||||Ja|  

## <a name="multidimensional-models"></a>Mehrdimensionale Modelle 
  
|Funktion|Enterprise|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|Entwickler|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Semiadditive Measures|Ja|Nein <sup>1</sup>|||||Ja|  
|Hierarchien|Ja|Ja|||||Ja|  
|KPIs (Key Performance Indicators)|Ja|Ja|||||Ja|  
|Perspektiven|Ja||||||Ja|  
|Aktionen|Ja|Ja|||||Ja|  
|Kontointelligenz|Ja|Ja|||||Ja|  
|Zeitintelligenz|Ja|Ja|||||Ja|  
|Benutzerdefinierte Rollups|Ja|Ja|||||Ja|  
|Cube-Rückschreiben|Ja|Ja|||||Ja|  
|Rückschreiben von Dimensionen|Ja||||||Ja|  
|Rückschreibezellen|Ja|Ja|||||Ja|  
|Drillthrough ausführen|Ja|Ja|||||Ja|  
|Erweiterte Hierarchietypen (Übergeordnet-Untergeordnet- und unregelmäßige Hierarchien)|Ja|Ja|||||Ja|  
|Erweiterte Dimensionen (Bezugsdimensionen, m:n-Dimensionen)|Ja|Ja|||||Ja|  
|Verknüpfte Measures und Dimensionen|Ja|Ja  <sup>2</sup> |||||Ja|  
|Translations|Ja|Ja|||||Ja|  
|Aggregations|Ja|Ja|||||Ja|  
|Mehrere Partitionen|Ja|Ja, bis zu 3|||||Ja|  
|Proaktives Zwischenspeichern|Ja||||||Ja|  
|Benutzerdefinierte Assemblys (gespeicherte Prozeduren)|Ja|Ja|||||Ja|  
|MDX-Abfragen und Skripts|Ja|Ja|||||Ja|  
|DAX-Abfragen|Ja|Ja|||||Ja|  
|Rollenbasiertes Sicherheitsmodell|Ja|Ja|||||Ja|  
|Sicherheit auf Dimensions- und Zellenebene|Ja|Ja|||||Ja|  
|Skalierbarer Zeichenfolgenspeicher|Ja|Ja|||||Ja|  
|MOLAP-, ROLAP- und HOLAP-Speichermodelle|Ja|Ja|||||Ja|  
|Binärer und komprimierter XML-Transport|Ja|Ja|||||Ja|  
|Pushmodus-Verarbeitung|Ja||||||Ja|  
|Measureausdrücke|Ja||||||Ja|  
  
 <sup>1</sup> Das semiadditive LastChild-Measure wird in der Standard Edition unterstützt, während andere semiadditive Measures, z. B. None, FirstChild, FirstNonEmpty, LastNonEmpty, AverageOfChildren und ByAccount, nicht unterstützt werden. Additive Measures, z. B. Sum, Count, Min, Max und nicht additive Measures (DistinctCount) werden in allen Editionen unterstützt.  
  <sup>2</sup> Die Standard Edition unterstützt Verknüpfen von Measures und Dimensionen innerhalb derselben Datenbank, jedoch nicht aus anderen Datenbanken oder Instanzen.
  
## <a name="power-pivot-for-sharepoint"></a>PowerPivot für SharePoint  
  
|Funktion|Enterprise|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|Entwickler|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|SharePoint-Farmintegration auf Grundlage der Shared Services-Architektur|Ja||||||Ja|  
|Verwendungsberichte|Ja||||||Ja|  
|Systemüberwachungsregeln|Ja||||||Ja|  
|Power Pivot-Katalog|Ja||||||Ja|  
|PowerPivot-Datenaktualisierung|Ja||||||Ja|  
|Power Pivot-Datenfeeds|Ja||||||Ja|  
  
## <a name="data-mining"></a>Data Mining  
  
|Funktionsname|Enterprise|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|Entwickler|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Standardalgorithmen|Ja|Ja|||||Ja|  
|Data Mining-Tools (Assistenten, Editoren, Abfrage-Generatoren)|Ja|Ja|||||Ja|  
|Kreuzvalidierung|Ja||||||Ja|  
|Modelle für gefilterte Teilmengen von Daten der Miningstruktur|Ja||||||Ja|  
|Zeitreihen: Benutzerdefinierte Kombination von ARTXP- und ARIMA-Methoden|Ja||||||Ja|  
|Zeitreihen: Vorhersage mit neuen Daten|Ja||||||Ja|  
|Unbegrenzte gleichzeitige Data Mining-Abfragen|Ja||||||Ja|  
|Erweiterte Konfigurations- und Optimierungsoptionen für Data Mining-Algorithmen|Ja||||||Ja|  
|Unterstützung für Plug-In-Algorithmen|Ja||||||Ja|  
|Parallele Modellverarbeitung|Ja||||||Ja|  
|Zeitreihen: reihenübergreifende Vorhersage|Ja||||||Ja|  
|Unbegrenzte Attribute für Zuordnungsregeln|Ja||||||Ja|  
|Sequenzvorhersage|Ja||||||Ja|  
|Mehrere Vorhersageziele für Naïve BaJa, neuronale Netzwerke und logistische Regression|Ja||||||Ja|  
  


