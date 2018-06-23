---
title: Spezifikationen der maximalen Kapazität (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], maximum number
- objects [Analysis Services], maximum size
ms.assetid: 49fe1673-b908-4c7a-88ff-415efd294d27
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 52c77297ad9b5db79f235611a4ddf47357445629
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148012"
---
# <a name="maximum-capacity-specifications-analysis-services"></a>Spezifikationen der maximalen Kapazität (Analysis Services)
  Die folgenden Tabellen geben die maximalen Größe und Anzahl verschiedener in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Komponenten definierter Objekte unter unterschiedlichen Serverbereitstellungsmodi an.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Mehrdimensionale und Datamining (DeploymentMode = 0)](#bkmk_OLAP)  
  
 [SharePoint (DeploymentMode = 1)](#bkmk_sharepoint)  
  
 [Tabellarisch (DeploymentMode = 2)](#bkmk_vertipaq)  
  
##  <a name="bkmk_OLAP"></a> Mehrdimensionale und Datamining (DeploymentMode = 0)  
 Der MOLAP-Speichermodus, der sowohl Daten als auch Metadaten speichert, verfügt über zusätzliche physische Grenzen für Dateigrößen. Zeichenfolgenspeicherdateien weisen standardmäßig eine maximale Größe von 4 GB auf. Wenn Sie größere Dateien für Zeichenfolgenspeicher benötigen, können Sie eine andere Zeichenfolgenspeicherarchitektur angeben. Weitere Informationen finden Sie unter [Zeichenfolgenspeicher für Dimensionen und Partitionen konfigurieren](../configure-string-storage-for-dimensions-and-partitions.md).  
  
|Objekt|Maximale Größe/Anzahl|  
|------------|----------------------------|  
|Datenbank in einer Instanz|2^31-1 = 2,147,483,647|  
|Dimensionen in einer Datenbank|2^31-1 = 2,147,483,647|  
|Attribute in einer Dimension|2^31-1 = 2,147,483,647|  
|Elemente in einem Dimensionsattribut|2^31-1 = 2,147,483,647|  
|Benutzerdefinierte Hierarchien in einer Dimension|2^31-1 = 2,147,483,647|  
|Ebenen in einer benutzerdefinierten Hierarchie|2^31-1 = 2,147,483,647|  
|Cubes in einer Datenbank|2^31-1 = 2,147,483,647|  
|Measuregruppen in einem Cube|2^31-1 = 2,147,483,647|  
|Measures in einer Measuregruppe|2^31-1 = 2,147,483,647|  
|Berechnungen in einem Cube|2^31-1 = 2,147,483,647|  
|KPIs in einem Cube|2^31-1 = 2,147,483,647|  
|Aktionen in einem Cube|2^31-1 = 2,147,483,647|  
|Partitionen in einem Cube|2^31-1 = 2,147,483,647|  
|Übersetzungen in einem Cube|2^31-1 = 2,147,483,647|  
|Aggregationen in einer Partition|2^31-1 = 2,147,483,647|  
|Von einer Abfrage zurückgegebene Zellen|2^31-1 = 2,147,483,647|  
|Datensatzgröße in der Quellabfrage|64 KB|  
|Die Länge von Objektnamen|100 Zeichen|  
|Maximale Anzahl unterschiedlicher Statusangaben in einer Attributspalte eines Data Mining-Modells|2^31-1 = 2,147,483,647|  
|Maximale Anzahl berücksichtigter Attribute (Funktionsauswahl)|2^31-1 = 2,147,483,647|  
  
 Weitere Informationen zu objektbenennungsrichtlinien finden Sie unter [ASSL-Objekte und-Objekteigenschaften](../scripting-language-assl/assl-objects-and-object-characteristics.md).  
  
 Weitere Informationen zu datenquellenbegrenzungen für online analytical Processing (OLAP) und Datamining finden Sie unter [unterstützte Datenquellen &#40;mehrdimensionale SSAS-&#41;](../supported-data-sources-ssas-multidimensional.md), [unterstützte Datenquellen &#40;SSAS – mehrdimensional&#41;](../supported-data-sources-ssas-multidimensional.md), und [ASSL-Objekte und-Objekteigenschaften](../scripting-language-assl/assl-objects-and-object-characteristics.md).  
  
##  <a name="bkmk_sharepoint"></a> SharePoint (DeploymentMode = 1)  
  
|Objekt|Maximale Größe/Anzahl|  
|------------|----------------------------|  
|Datenbank in einer Instanz|2^31-1 = 2,147,483,647|  
|Tabellen in einer Datenbank|2^31-1 = 2,147,483,647|  
|Spalten in einer Tabelle|2 ^ 31-1 = 2,147,483,647 **Warnung:** Gesamtanzahl der Spalten in einer Tabelle hängt von der Gesamtzahl von Measures und berechneten Spalten derselben Tabelle zugeordnet sind. Die maximale Anzahl von 'Spalten + Measures + berechnete Spalten' für eine Tabelle ist 2^31-1 = 2,147,483,647|  
|Zeilen in einer Tabelle|Unbegrenzte **Warnung:** mit der Einschränkung, dass keine einzelne Spalte nicht mehr als 1.999.999.997 unterschiedliche Werte enthalten kann.|  
|Hierarchien in einer Tabelle|2^31-1 = 2,147,483,647|  
|Ebenen in einer Hierarchie|2^31-1 = 2,147,483,647|  
|Beziehungen|2^31-1 = 2,147,483,647|  
|Schlüsselspalten in einer Tabelle|2^31-1 = 2,147,483,647|  
|Measures in einer Tabelle|2 ^ 31-1 = 2,147,483,647 **Warnung:** Gesamtzahl von Measures in einer Tabelle hängt von der Gesamtanzahl der Spalten und berechneten Spalten derselben Tabelle zugeordnet sind. Die maximale Anzahl von 'Spalten + Measures + berechnete Spalten' für eine Tabelle ist 2^31-1 = 2,147,483,647|  
|Berechnete Spalten in einer Tabelle|2 ^ 31-1 = 2,147,483,647 **Warnung:** Gesamtzahl der berechneten Spalten in einer Tabelle hängt von der Gesamtanzahl der Spalten und Measures, die der gleichen Tabelle zugeordnet sind. Die maximale Anzahl von 'Spalten + Measures + berechnete Spalten' für eine Tabelle ist 2^31-1 = 2,147,483,647|  
|Von einer Abfrage zurückgegebene Zellen|2^31-1 = 2,147,483,647|  
|Datensatzgröße in der Quellabfrage|64 KB|  
|Die Länge von Objektnamen|100 Zeichen|  
  
##  <a name="bkmk_vertipaq"></a> Tabellarisch (DeploymentMode = 2)  
  
|Objekt|Maximale Größe/Anzahl|  
|------------|----------------------------|  
|Datenbank in einer Instanz|2^31-1 = 2,147,483,647|  
|Tabellen in einer Datenbank|2^31-1 = 2,147,483,647|  
|Spalten in einer Tabelle|2 ^ 31-1 = 2,147,483,647 **Warnung:** Gesamtanzahl der Spalten in einer Tabelle hängt von der Gesamtzahl von Measures und berechneten Spalten derselben Tabelle zugeordnet sind. Die maximale Anzahl von 'Spalten + Measures + berechnete Spalten' für eine Tabelle ist 2^31-1 = 2,147,483,647|  
|Zeilen in einer Tabelle|Unbegrenzte **Warnung:** mit der Einschränkung, dass eine einzelne Spalte in der Tabelle nicht mehr als 1.999.999.997 unterschiedliche Werte haben kann.|  
|Hierarchien in einer Tabelle|2^31-1 = 2,147,483,647|  
|Ebenen in einer Hierarchie|2^31-1 = 2,147,483,647|  
|Beziehungen|2^31-1 = 2,147,483,647|  
|Schlüsselspalten in einer Tabelle|2^31-1 = 2,147,483,647|  
|Measures in einer Tabelle|2 ^ 31-1 = 2,147,483,647 **Warnung:** Gesamtzahl von Measures in einer Tabelle hängt von der Gesamtanzahl der Spalten und berechneten Spalten derselben Tabelle zugeordnet sind. Die maximale Anzahl von 'Spalten + Measures + berechnete Spalten' für eine Tabelle ist 2^31-1 = 2,147,483,647|  
|Berechnete Spalten in einer Tabelle|2 ^ 31-1 = 2,147,483,647 **Warnung:** Gesamtzahl der berechneten Spalten in einer Tabelle hängt von der Gesamtanzahl der Spalten und Measures, die der gleichen Tabelle zugeordnet sind. Die maximale Anzahl von 'Spalten + Measures + berechnete Spalten' für eine Tabelle ist 2^31-1 = 2,147,483,647|  
|Von einer Abfrage zurückgegebene Zellen|2^31-1 = 2,147,483,647|  
|Datensatzgröße in der Quellabfrage|64 KB|  
|Die Länge von Objektnamen|100 Zeichen|  
  
## <a name="see-also"></a>Siehe auch  
 [Bestimmen des Servermodus einer Analysis Services-Instanz](../../instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Allgemeine Eigenschaften](../../server-properties/general-properties.md)  
  
  