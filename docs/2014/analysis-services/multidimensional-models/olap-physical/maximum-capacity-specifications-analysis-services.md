---
title: Spezifikationen der maximalen Kapazität (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], maximum number
- objects [Analysis Services], maximum size
ms.assetid: 49fe1673-b908-4c7a-88ff-415efd294d27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 561cbbb64734c117b295ca6d97420b6980fa5428
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62725494"
---
# <a name="maximum-capacity-specifications-analysis-services"></a>Spezifikationen der maximalen Kapazität (Analysis Services)
  Die folgenden Tabellen geben die maximalen Größe und Anzahl verschiedener in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Komponenten definierter Objekte unter unterschiedlichen Serverbereitstellungsmodi an.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Mehrdimensional und Data Mining (DeploymentMode=0)](#bkmk_OLAP)  
  
 [SharePoint (DeploymentMode=1)](#bkmk_sharepoint)  
  
 [Tabellarisch (DeploymentMode=2)](#bkmk_vertipaq)  
  
##  <a name="bkmk_OLAP"></a>Mehrdimensional und Data Mining (deploymentmode = 0)  
 Der MOLAP-Speichermodus, der sowohl Daten als auch Metadaten speichert, verfügt über zusätzliche physische Grenzen für Dateigrößen. Zeichenfolgenspeicherdateien weisen standardmäßig eine maximale Größe von 4 GB auf. Wenn Sie größere Dateien für Zeichenfolgenspeicher benötigen, können Sie eine andere Zeichenfolgenspeicherarchitektur angeben. Weitere Informationen finden Sie unter [Konfigurieren des Zeichen folgen Speichers für Dimensionen und Partitionen](../configure-string-storage-for-dimensions-and-partitions.md).  
  
|Object|Maximale Größe/Anzahl|  
|------------|----------------------------|  
|Datenbanken in einer Instanz|2^31-1 = 2.147483.647|  
|Dimensionen in einer Datenbank|2^31-1 = 2.147483.647|  
|Attribute in einer Dimension|2^31-1 = 2.147483.647|  
|Elemente in einem Dimensionsattribut|2^31-1 = 2.147483.647|  
|Benutzerdefinierte Hierarchien in einer Dimension|2^31-1 = 2.147483.647|  
|Ebenen in einer benutzerdefinierten Hierarchie|2^31-1 = 2.147483.647|  
|Cubes in einer Datenbank|2^31-1 = 2.147483.647|  
|Measuregruppen in einem Cube|2^31-1 = 2.147483.647|  
|Measures in einer Measuregruppe|2^31-1 = 2.147483.647|  
|Berechnungen in einem Cube|2^31-1 = 2.147483.647|  
|KPIs in einem Cube|2^31-1 = 2.147483.647|  
|Aktionen in einem Cube|2^31-1 = 2.147483.647|  
|Partitionen in einem Cube|2^31-1 = 2.147483.647|  
|Übersetzungen in einem Cube|2^31-1 = 2.147483.647|  
|Aggregationen in einer Partition|2^31-1 = 2.147483.647|  
|Von einer Abfrage zurückgegebene Zellen|2^31-1 = 2.147483.647|  
|Datensatzgröße der Quellabfrage|64 KB|  
|Länge des Objektnamens|100 Zeichen|  
|Maximale Anzahl unterschiedlicher Statusangaben in einer Attributspalte eines Data Mining-Modells|2^31-1 = 2.147483.647|  
|Maximale Anzahl berücksichtigter Attribute (Funktionsauswahl)|2^31-1 = 2.147483.647|  
  
 Weitere Informationen zu Benennungs Richtlinien für Objekte finden Sie unter [ASSL-Objekte und Objektmerkmale](../scripting-language-assl/assl-objects-and-object-characteristics.md).  
  
 Weitere Informationen zu Datenquellen Einschränkungen für die analytische Online Verarbeitung (Online Analytical Processing, OLAP) und Data Mining finden Sie unter [unterstützte Datenquellen &#40;SSAS-multidimensionalen&#41;](../supported-data-sources-ssas-multidimensional.md), [unterstützte Datenquellen &#40;SSAS Multidimensional&#41;](../supported-data-sources-ssas-multidimensional.md)und [ASSL-Objekte und Objektmerkmale](../scripting-language-assl/assl-objects-and-object-characteristics.md).  
  
##  <a name="bkmk_sharepoint"></a>SharePoint (deploymentmode = 1)  
  
|Object|Maximale Größe/Anzahl|  
|------------|----------------------------|  
|Datenbanken in einer Instanz|2^31-1 = 2.147483.647|  
|Tabellen in einer Datenbank|2^31-1 = 2.147483.647|  
|Spalten in einer Tabelle|2 ^ 31-1 = 2.147.483.647 **Warnung:** die Gesamtzahl der Spalten in einer Tabelle hängt von der Gesamtanzahl der Measures und der berechneten Spalten ab, die der gleichen Tabelle zugeordnet sind. Die maximale Anzahl von 'Spalten + Measures + berechnete Spalten' für eine Tabelle ist 2^31-1 = 2,147,483,647|  
|Zeilen in einer Tabelle|Unbegrenzte **Warnung:** mit der Einschränkung, dass eine einzelne Spalte möglicherweise mehr als 1.999.999.997 unterschiedliche Werte enthält.|  
|Hierarchien in einer Tabelle|2^31-1 = 2.147483.647|  
|Ebenen in einer Hierarchie|2^31-1 = 2.147483.647|  
|Beziehungen|2^31-1 = 2.147483.647|  
|Schlüsselspalten in einer Tabelle|2^31-1 = 2.147483.647|  
|Measures in einer Tabelle|2 ^ 31-1 = 2.147.483.647 **Warnung:** die Gesamtanzahl der Measures in einer Tabelle hängt von der Gesamtzahl der Spalten und der berechneten Spalten ab, die der gleichen Tabelle zugeordnet sind. Die maximale Anzahl von 'Spalten + Measures + berechnete Spalten' für eine Tabelle ist 2^31-1 = 2,147,483,647|  
|Berechnete Spalten in einer Tabelle|2 ^ 31-1 = 2.147.483.647 **Warnung:** die Gesamtzahl der berechneten Spalten in einer Tabelle hängt von der Gesamtanzahl der Spalten und Measures ab, die der gleichen Tabelle zugeordnet sind. Die maximale Anzahl von 'Spalten + Measures + berechnete Spalten' für eine Tabelle ist 2^31-1 = 2,147,483,647|  
|Von einer Abfrage zurückgegebene Zellen|2^31-1 = 2.147483.647|  
|Datensatzgröße der Quellabfrage|64 KB|  
|Länge des Objektnamens|100 Zeichen|  
  
##  <a name="bkmk_vertipaq"></a>Tabellarisch (deploymentmode = 2)  
  
|Object|Maximale Größe/Anzahl|  
|------------|----------------------------|  
|Datenbanken in einer Instanz|2^31-1 = 2.147483.647|  
|Tabellen in einer Datenbank|2^31-1 = 2.147483.647|  
|Spalten in einer Tabelle|2 ^ 31-1 = 2.147.483.647 **Warnung:** die Gesamtzahl der Spalten in einer Tabelle hängt von der Gesamtanzahl der Measures und der berechneten Spalten ab, die der gleichen Tabelle zugeordnet sind. Die maximale Anzahl von 'Spalten + Measures + berechnete Spalten' für eine Tabelle ist 2^31-1 = 2,147,483,647|  
|Zeilen in einer Tabelle|Unbegrenzte **Warnung:** mit der Einschränkung, dass eine einzelne Spalte in der Tabelle mehr als 1.999.999.997 unterschiedliche Werte aufweisen kann.|  
|Hierarchien in einer Tabelle|2^31-1 = 2.147483.647|  
|Ebenen in einer Hierarchie|2^31-1 = 2.147483.647|  
|Beziehungen|2^31-1 = 2.147483.647|  
|Schlüsselspalten in einer Tabelle|2^31-1 = 2.147483.647|  
|Measures in einer Tabelle|2 ^ 31-1 = 2.147.483.647 **Warnung:** die Gesamtanzahl der Measures in einer Tabelle hängt von der Gesamtzahl der Spalten und der berechneten Spalten ab, die der gleichen Tabelle zugeordnet sind. Die maximale Anzahl von 'Spalten + Measures + berechnete Spalten' für eine Tabelle ist 2^31-1 = 2,147,483,647|  
|Berechnete Spalten in einer Tabelle|2 ^ 31-1 = 2.147.483.647 **Warnung:** die Gesamtzahl der berechneten Spalten in einer Tabelle hängt von der Gesamtanzahl der Spalten und Measures ab, die der gleichen Tabelle zugeordnet sind. Die maximale Anzahl von 'Spalten + Measures + berechnete Spalten' für eine Tabelle ist 2^31-1 = 2,147,483,647|  
|Von einer Abfrage zurückgegebene Zellen|2^31-1 = 2.147483.647|  
|Datensatzgröße der Quellabfrage|64 KB|  
|Länge des Objektnamens|100 Zeichen|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bestimmen des Server Modus einer Analysis Services Instanz](../../instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Allgemeine Eigenschaften](../../server-properties/general-properties.md)  
  
  
