---
title: Tabellarische Analysis Services-Modellen in Excel analysieren | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: abd910573f512e32ee58c6c3afabac17664f4b24
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207757"
---
# <a name="analyze-in-excel"></a>In Excel analysieren
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Die Funktion in Excel analysieren, in SSDT-Entwickler von tabellarischen Modellen bietet eine Möglichkeit, die schnelle Analyse von Modellprojekten während der Entwicklung. Über die Funktion In Excel analysieren wird Microsoft Excel geöffnet; sie stellt eine Datenquellenverbindung mit der Arbeitsbereichsdatenbank des Modells her und fügt automatisch eine PivotTable in das Arbeitsblatt ein. Objekte der Arbeitsbereichsdatenbank (Tabellen, Spalten und Measures) sind als Felder in der PivotTable-Feldliste enthalten. Objekte und Daten können dann innerhalb des Kontexts des effektiven Benutzers oder der Rolle und Perspektive angezeigt werden.  
  
 In diesem Artikel wird davon ausgegangen, dass Sie bereits mit Microsoft Excel, PivotTables und PivotCharts vertraut sind. Weitere Informationen zur Verwendung von Excel finden Sie in der Excel-Hilfe.  
  
##  <a name="bkmk_benefits"></a> Vorteile  
 Die Funktion In Excel analysieren bietet Modellentwicklern die Möglichkeit, die Effizienz eines Modellprojekts unter Verwendung der verbreiteten Datenanalyseanwendung Microsoft Excel zu testen. Um die Funktion in Excel analysieren zu verwenden, Sie müssen Microsoft Office 2003 oder höher auf demselben Computer wie SSDT installiert.  
  
 Durch die Funktion In Excel analysieren wird Excel geöffnet und eine neue Excel-Arbeitsmappe (.xls) erstellt. Eine Datenverbindung von der Arbeitsmappe zur Modellarbeitsbereichsdatenbank wird erstellt. Dem Arbeitsblatt wird eine leere PivotTable hinzugefügt, und die PivotTable-Feldliste wird mit Modellobjektmetadaten aufgefüllt. Sie können der PivotTable anschließend Anzeigedaten und Slicer hinzufügen.  
  
 Wenn die Funktion In Excel analysieren mit der Standardeinstellung verwendet wird, entspricht das aktuell angemeldete Benutzerkonto dem effektiven Benutzer. Dieses Konto ist in der Regel ein Administrator und verfügt über keinerlei Einschränkungen für die Modellierung von Objekten oder Daten. Sie können jedoch einen anderen effektiven Benutzernamen oder eine Rolle angeben. Auf diese Weise können Sie ein Modellprojekt in Excel innerhalb des Kontexts eines spezifischen Benutzers bzw. einer spezifischen Rolle durchsuchen. Für das Festlegen des effektiven Benutzers stehen folgende Optionen zur Verfügung:  
  
 **Aktueller Windows-Benutzer**  
 Verwendet das Benutzerkonto, unter dem Sie gerade angemeldet sind.  
  
 **Anderer Windows-Benutzer**  
 Verwendet einen angegebenen Windows-Benutzernamen anstatt den Namen des aktuell angemeldeten Benutzers. Zur Verwendung eines anderen Windows-Benutzers ist kein Kennwort erforderlich. Objekte und Daten können nur in Excel innerhalb des Kontexts des effektiven Benutzernamens angezeigt werden. In Excel können keine Änderungen an Modellobjekten oder -daten vorgenommen werden.  
  
 **Rolle**  
 Eine Rolle wird verwendet, um Benutzerberechtigungen für die Objektmetadaten und die Daten zu definieren. Rollen werden normalerweise für einen bestimmten Windows-Benutzer oder eine Windows-Benutzergruppe definiert. Bestimmte Rollen können zusätzliche Filter auf Zeilenebene einschließen, die in einer DAX-Formel definiert sind. Wenn Sie die Funktion In Excel analysieren verwenden, können Sie optional eine zu verwendende Rolle auswählen. Objektmetadaten und Datensichten werden durch Berechtigungen und Filter eingeschränkt, die für die Rolle definiert sind. Weitere Informationen finden Sie unter [erstellen und Verwalten von Rollen](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md).  
  
 Zusätzlich zum effektiven Benutzer oder der Rolle können Sie eine Perspektive angeben. Perspektiven ermöglichen Modellentwicklern die Definition von Modellobjekt- und Datensichten für bestimmte Geschäftsszenarien. Standardmäßig wird keine Perspektive verwendet. Um eine Perspektive mit in Excel analysieren verwenden, müssen Perspektiven bereits mit dem Dialogfeld Perspektiven in SSDT definiert werden. Wenn eine Perspektive angegeben wird, enthält die PivotTable-Liste nur die in der Perspektive ausgewählten Objekte. Weitere Informationen finden Sie unter [erstellen und Verwalten von Perspektiven](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md).  
  
##  <a name="bkmk_rt"></a> Related tasks  
  
|**Thema**|**Beschreibung**|  
|---------------|---------------------|  
|[Analysieren eines tabellarischen Modells in Excel](../../analysis-services/tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md)|Dieser Artikel beschreibt, wie Sie die analysieren in Excel-Funktion im Modell-Designer verwenden, um Excel zu öffnen, erstellen eine datenquellenverbindung mit der arbeitsbereichsdatenbank des Modells und eine PivotTable zum Arbeitsblatt hinzuzufügen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysieren eines Tabellenmodells in Excel](../../analysis-services/tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md)   
 [Rollen](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [Perspektiven](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)  
  
  
