---
title: Argumente und Eigenschaften von gespeicherten Prozeduren für räumliche Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- spatial indexes [SQL Server], stored procedures
ms.assetid: ee26082b-c0ed-40ff-b5ad-f5f6b00f0475
author: stevestein
ms.author: sstein
ms.openlocfilehash: 82b906be4568b15a18c55247532bf35b6cd939a7
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028899"
---
# <a name="spatial-index-stored-procedures---arguments-and-properties"></a>Gespeicherte Prozeduren für räumliche Indizes: Argumente und Eigenschaften
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In diesem Thema sind die Argumente und Eigenschaften gespeicherter Prozeduren für Räumlichkeitsindizes dokumentiert.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
 Die Syntax bestimmter gespeicherter Prozeduren für Räumlichkeitsindizes finden Sie in den folgenden Themen:  
  
-   [sp_help_spatial_geometry_index &#40;(Transact-SQL)&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)  
  
-   [sp_help_spatial_geometry_index_xml &#40;(Transact-SQL)&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-xml-transact-sql.md)  
  
-   [sp_help_spatial_geography_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)  
  
-   [sp_help_spatial_geography_index_xml &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-xml-transact-sql.md)  
  
## <a name="arguments"></a>Argumente  
`[ @tabname = ] 'tabname'`Der qualifizierte oder nicht qualifizierte Name der Tabelle, für die der räumliche Index angegeben wurde.  
  
 Anführungszeichen sind nur dann erforderlich, wenn eine qualifizierte Tabelle angegeben wird. Bei Angabe eines vollqualifizierten Namens, einschließlich eines Datenbanknamens, muss es sich bei dem Datenbanknamen um den Namen der aktuellen Datenbank handeln. *tabname* ist vom Datentyp **nvarchar**(776) und hat keinen Standardwert.  
  
`[ @indexname = ] 'indexname'`Der Name des angegebenen räumlichen Indexes. *Indexname* ist vom **Datentyp vom Datentyp sysname** und hat keinen Standardwert.  
  
`[ @verboseoutput = ] 'verboseoutput'`Der Bereich von Eigenschaftsnamen und-Werten, die zurückgegeben werden sollen.  
  
 0 = Haupteigenschaften  
  
 \>0 = alle Eigenschaften  
  
 *verbotenoutput* ist vom Datentyp **tinyint** und hat keinen Standardwert.  
  
`[ @query_sample = ] 'query_sample'`Ist ein repräsentatives Abfrage Beispiel, das verwendet werden kann, um die Nützlichkeit des Indexes zu testen. Dabei kann es sich um ein repräsentatives Objekt oder ein Abfragefenster handeln. *query_sample* ist vom Typ **Geometry** und hat keinen Standardwert.  
  
`[ @xml_output = ] 'xml_output'`Ein Ausgabeparameter, der das Resultset in einem XML-Fragment zurückgibt. *xml_output* ist vom Typ **XML** und hat keinen Standardwert.  
  
## <a name="properties"></a>Eigenschaften  
 Legen Sie  **\@verboseoutput** = 0 so fest, dass Kerneigenschaften zurückgegeben werden, wie in der folgenden Tabelle dargestellt. Verbo* Output > 0, um alle Eigenschaften des räumlichen Indexes zurückzugeben.  **\@**  
  
 **Base_Table_Rows**  
 Anzahl der Zeilen in der Basistabelle. Der Wert ist " **bigint**".  
  
 **Bounding_Box_xmin**  
 X-minimale Begrenzungsfeld Eigenschaften des räumlichen Indexes für den **Geometry** -Typ. Dieser Eigenschafts Wert ist für den **geography**-Typ NULL. Der Wert ist " **float**".  
  
 **Bounding_Box_ymin**  
 Y-minimale Begrenzungsfeld Eigenschaften des räumlichen Indexes für den **Geometry** -Typ. Dieser Eigenschafts Wert ist für den **geography** -Typ NULL. Der Wert ist " **float**".  
  
 **Bounding_Box_xmax**  
 X-maximale Begrenzungsfeld Eigenschaften des räumlichen Indexes für den **Geometry** -Typ. Dieser Eigenschafts Wert ist für den **geography** -Typ NULL. Der Wert ist " **float**".  
  
 **Bounding_Box_ymax**  
 Y-maximale Eigenschaften für Begrenzungs Felder des räumlichen Indexes für den **Geometry** -Typ. Dieser Eigenschafts Wert ist für den **geography** -Typ NULL. Der Wert ist " **float**".  
  
 **Grid_Size_Level_1**  
 Die Raster Dichte der Ebene 1 des räumlichen Indexes:  
  
 16 für LOW  
  
 64 für MEDIUM  
  
 256 für HIGH  
  
 Der Wert ist " **int**".  
  
 **Grid_Size_Level_2**  
 Die Raster Dichte der Ebene 2 des räumlichen Indexes:  
  
 16 für LOW  
  
 64 für MEDIUM  
  
 256 für HIGH  
  
 Der Wert ist " **int**".  
  
 **Grid_Size_Level_3**  
 Die Raster Dichte der Ebene 3 des räumlichen Indexes:  
  
 16 für LOW  
  
 64 für MEDIUM  
  
 256 für HIGH  
  
 Der Wert ist " **int**".  
  
 **Grid_Size_Level_4**  
 Rasterdichte der Ebene 4 des Räumlichkeitsindex:  
  
 16 für LOW  
  
 64 für MEDIUM  
  
 256 für HIGH  
  
 Der Wert ist " **int**".  
  
 **Cells_Per_Object**  
 Anzahl der Zellen pro Objekt (Indexeigenschaft). Der Wert ist " **int**".  
  
 **Total_Primary_Index_Rows**  
 Anzahl der Zeilen im Index. Der Wert ist " **bigint**".  
  
 **Total_Primary_Index_Pages**  
 Anzahl der Seiten im Index. Der Wert ist " **bigint**".  
  
 **Average_Number_Of_Index_Rows_Per_Base_Row**  
 Anzahl der Indexzeilen/Anzahl der Basistabellenzeilen. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_ObjectCells_In_Level0_For_QuerySample**  
 Gibt an, ob das repräsentative Abfrage Beispiel außerhalb des umgebenden Felds des **Geometry** -Indexes und in der Stammzelle (Zelle der Ebene 0) liegt. Dies ist entweder 0 (nicht in Zelle der Ebene 0) oder 1. Befindet es sich in der Zelle der Ebene 0, ist der untersuchte Index nicht für das Abfragebeispiel geeignet. Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_ObjectCells_In_Level0_In_Index**  
 Anzahl der Zellen Instanzen indizierter Objekte, die sich auf Ebene 0 (Stammzelle, außerhalb des umgebenden Felds für die **Geometrie**befinden) im Mosaik Prozess befinden. Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 Bei **Geometry** -Indizes wird dies ausgelöst, wenn das Begrenzungsfeld des Indexes kleiner als die Daten Domäne ist. Eine große Anzahl von Objekten in Ebene 0 erfordert möglicherweise sekundäre Filter, wenn das Abfragefenster teilweise außerhalb des umgebenden Felds liegt und die Index Leistung verringert (z. b. **Total_Number_Of_ObjectCells_In_Level0_For_QuerySample** ist 1). Wenn das Abfragefenster innerhalb des umgebenden Felds liegt, kann eine hohe Anzahl an Objekten in Ebene 0 die Leistung des Indexes tatsächlich verbessern.  
  
 NULL und leere Instanzen werden auf Ebene 0 gezählt, wirken sich aber nicht auf die Leistung aus. Ebene 0 hat so viele Zellen wie NULL und leere Instanzen in der Basistabelle. Bei **geografieindizes** hat Ebene 0 so viele Zellen wie NULL und leere Instanzen + 1 Zelle, da das Abfrage Beispiel als 1 gezählt wird.  
  
 **Total_Number_Of_ObjectCells_In_Level1_In_Index**  
 Anzahl der Zellen Instanzen indizierter Objekte, die im Mosaik Prozess mit der Genauigkeit der Ebene 1 verwendet werden. Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_ObjectCells_In_Level2_In_Index**  
 Anzahl der Zellen Instanzen indizierter Objekte, die mit der Genauigkeit der Ebene 2 im Mosaik Prozess berücksichtigt werden. Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_ObjectCells_In_Level3_In_Index**  
 Anzahl der Zellen Instanzen indizierter Objekte, die mit der Genauigkeit der Ebene 3 im Mosaik Prozess berücksichtigt werden. Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_ObjectCells_In_Level4_In_Index**  
 Anzahl der Zelleninstanzen indizierter Objekte, die im Mosaikprozess mit dem Genauigkeitsgrad 4 berücksichtigt werden. Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_interior_ObjectCells_In_Level1_In_Index**  
 Anzahl der Zellen, die vollständig von einem Objekt auf Mosaik Ebene 1 abgedeckt werden und daher im Inneren des Objekts sind. (Cell_attributevalue ist 2.) Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_interior_ObjectCells_In_Level2_In_Index**  
 Anzahl der Zellen, die vollständig von einem Objekt auf Mosaik Ebene 2 abgedeckt werden und daher im Inneren des Objekts sind. (Cell_attribute-Wert ist 2.) Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_interior_ObjectCells_In_Level3_In_Index**  
 Anzahl der Zellen, die vollständig von einem Objekt auf Mosaik Ebene 3 abgedeckt werden und daher im Inneren des Objekts sind. (Cell_attribute-Wert ist 2.) Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_interior_ObjectCells_In_Level4_In_Index**  
 Anzahl der Zellen, die vollständig von einem Objekt auf Mosaikebene 4 abgedeckt werden und daher im Inneren des Objekts liegen. (Cell_attribute-Wert ist 2.) Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level1_In_Index**  
 Anzahl der Zellen, die von einem Objekt auf Mosaik Ebene 1 geschnitten werden. (Cell_attribute-Wert ist 1.) Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level2_In_Index**  
 Anzahl der Zellen, die von einem Objekt auf Mosaik Ebene 2 geschnitten werden. (Cell_attribute-Wert ist 1.) Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level3_In_Index**  
 Anzahl der Zellen, die von einem Objekt auf Mosaik Ebene 3 geschnitten werden. (Cell_attribute-Wert ist 1.) Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level4_In_Index**  
 Anzahl der Zellen, die von einem Objekt auf Mosaikebene 4 geschnitten werden. (Cell_attribute-Wert ist 1.) Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_Border_ObjectCells_In_Level0_For_QuerySample**  
 Gibt an, ob sich das Abfragebeispiel in Stammzelle 0 außerhalb des umgebenden Felds befindet, dieses aber berührt. Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
> [!NOTE]  
>  Diese Informationen sind nur hilfreich, um zu ermitteln, ob Objekte vorhanden sind, die nur knapp neben dem umgebenden Feld liegen.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level0_In_Index**  
 Anzahl der Objekte in Ebene 0, die das umgebende Feld berühren. (Cell_attribute-Wert ist 0.)  Der Wert ist " **bigint**".  
  
 **Total_Number_Of_Border_ObjectCells_In_Level1_In_Index**  
 Anzahl von Objekt Zellen, die eine Rasterzellen Grenze auf der Mosaik Ebene 1 berühren. (Cell_attribute-Wert ist 0.) Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_Border_ObjectCells_In_Level2_In_Index**  
 Anzahl von Objekt Zellen, die eine Rasterzellen Grenze auf der Mosaik Ebene 2 berühren. (Cell_attribute-Wert ist 0.) Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_Border_ObjectCells_In_Level3_In_Index**  
 Anzahl von Objekt Zellen, die eine Rasterzellen Grenze auf der Mosaik Ebene 3 berühren. (Cell_attribute-Wert ist 0.) Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Total_Number_Of_Border_ObjectCells_In_Level4_In_Index**  
 Anzahl der Objektzellen, die eine Rasterzellenbegrenzung auf Mosaikebene 4 berühren. (Cell_attribute-Wert ist 0.) Dies ist eine Haupteigenschaft. Der Wert ist " **bigint**".  
  
 **Interior_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**  
 Prozentsatz des Gesamtbereichs (Summe der Blattzellen) des Rasters, der Blattzellen enthält, die durch ein Objekt abgedeckt werden.  
  
 Beispiel: Ein Objekt wird dem Mosaikprozess unterzogen und in zehn Zellen auf vier verschiedenen Rasterebenen zerlegt, die einen Bereich abdecken, der insgesamt 100 Blattzellen entspricht. Angenommen, es gibt drei innere Zellen, die vollständig durch das Objekt abgedeckt werden. Der durch die drei inneren Zellen abgedeckte Bereich entspricht 42 Blattzellen. Somit liegt der Prozentsatz an abgedecktem Bereich bei 42 Prozent. Dies ist ein gutes Maß dafür, wie gut die Objekte im Index aufgeteilt sind.  
  
 Der Wert ist " **float**".  
  
 **Intersecting_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**  
 Identisch mit **Interior_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**, mit der Ausnahme, dass es sich hierbei um teilweise behandelte Zellen handelt. Der Wert ist " **float**".  
  
 **Border_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**  
 Identisch mit **Interior_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage** , außer dass es sich hierbei um Rahmen Zellen handelt. Der Wert ist " **float**".  
  
 **Average_Cells_Per_Object_Normalized_To_Leaf_Grid**  
 Durchschnittliche Anzahl der Zellen pro Objekt, die auf das Blattraster normalisiert sind. Damit erhalten wir einen Anhaltspunkt zur räumlichen Größe des Objekts oder zur Größe der Objekte. Der Wert ist " **float**".  
  
 **Average_Objects_PerLeaf_GridCell**  
 Geringe Dichte des Index. Durchschnittliche Anzahl der Objekte pro Blattzelle. Der Wert ist " **float**".  
  
 **Number_Of_SRIDs_Found**  
 Anzahl der eindeutigen SRIDs im Index und in der Spalte. Der Wert ist " **int**".  
  
 Da eine Spalte mehrere SRIDs enthalten kann und sich Objekte mit unterschiedlichen SRIDs niemals schneiden, gibt die Anzahl der SRIDs die Selektivität des Indexes an.  
  
 **Width_Of_Cell_In_Level1**  
 Breiteneigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird vom Index bereitgestellt und ist von der SRID der indizierten Daten abhängig. Der Wert ist " **float**".  
  
 **Width_Of_Cell_In_Level2**  
 Breiteneigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird vom Index bereitgestellt und ist von der SRID der indizierten Daten abhängig. Der Wert ist " **float**".  
  
 **Width_Of_Cell_In_Level3**  
 Breiteneigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird vom Index bereitgestellt und ist von der SRID der indizierten Daten abhängig. Der Wert ist " **float**".  
  
 **Width_Of_Cell_In_Level4**  
 Breiteneigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird durch den Index vorgegeben und hängt von der SRID der indizierten Daten ab. Der Wert ist " **float**".  
  
 **Height_Of_Cell_In_Level1**  
 Höheneigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird vom Index bereitgestellt und ist von der SRID der indizierten Daten abhängig. Der Wert ist " **float**".  
  
 **Height_Of_Cell_In_Level2**  
 Höheneigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird vom Index bereitgestellt und ist von der SRID der indizierten Daten abhängig. Der Wert ist " **float**".  
  
 **Height_Of_Cell_In_Level3**  
 Höheneigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird vom Index bereitgestellt und ist von der SRID der indizierten Daten abhängig. Der Wert ist " **float**".  
  
 **Height_Of_Cell_In_Level4**  
 Höheneigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird vom Index bereitgestellt und ist von der SRID der indizierten Daten abhängig. Der Wert ist " **float**".  
  
 **Area_Of_Cell_In_Level1**  
 Bereichseigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird vom Index bereitgestellt und ist von der SRID der indizierten Daten abhängig. Der Wert ist " **float**".  
  
 **Area_Of_Cell_In_Level2**  
 Bereichseigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird vom Index bereitgestellt und ist von der SRID der indizierten Daten abhängig. Der Wert ist " **float**".  
  
 **Area_Of_Cell_In_Level3**  
 Bereichseigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird vom Index bereitgestellt und ist von der SRID der indizierten Daten abhängig. Der Wert ist " **float**".  
  
 **Area_Of_Cell_In_Level4**  
 Bereichseigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird vom Index bereitgestellt und ist von der SRID der indizierten Daten abhängig. Der Wert ist " **float**".  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level1**  
 Der Prozentsatz der Abdeckung des umgebenden Felds durch eine Zelle der Ebene 1. Der Wert ist " **float**".  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level2**  
 Der Prozentsatz der Abdeckung des umgebenden Felds durch eine Zelle der Ebene 2. Der Wert ist " **float**".  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level3**  
 Der Prozentsatz der Abdeckung des Begrenzungs Rahmens durch eine Zelle der Ebene 3. Der Wert ist " **float**".  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level4**  
 Der Prozentsatz der Abdeckung des umgebenden Felds durch eine Zelle der Ebene 4. Der Wert ist " **float**".  
  
 **Number_Of_Rows_Selected_By_Primary_Filter**  
 Anzahl der durch den primären Filter ausgewählten Zeilen. Dies ist eine Haupteigenschaft. Der Wert ist " **bigint".**  
  
 **Number_Of_Rows_Selected_By_Internal_Filter**  
 Anzahl der durch den internen Filter ausgewählten Zeilen. Der sekundäre Filter wird für diese Zeilen nicht aufgerufen. Dies ist eine Haupteigenschaft. Der Wert ist " **bigint".**  
  
 Die zurückgegebene Zahl ist nur für " **stintersekten**" anwendbar.  
  
 **Number_Of_Times_Secondary_Filter_Is_Called**  
 Anzahl der Aufrufe des sekundären Filters. Dies ist eine Haupteigenschaft. Der Wert ist " **bigint".**  
  
 **Percentage_Of_Rows_NotSelected_By_Primary_Filter**  
 Wenn N Zeilen in der Basistabelle enthalten sind und P durch den primären Filter ausgewählt werden, gibt dies (N-P)/N als Prozentsatz zurück. Dies ist eine Haupteigenschaft. Der Wert ist " **float".**  
  
 **Percentage_Of_Primary_Filter_Rows_Selected_By_internal_Filter**  
 Wenn P Zeilen durch den primären Filter und S Zeilen durch den internen Filter ausgewählt werden, gibt dies S/P als Prozentsatz zurück. Je höher der Prozentsatz, desto besser kann der Index den leistungsintensiveren sekundären Filter vermeiden. Dies ist eine Haupteigenschaft. Der Wert ist " **float".**  
  
 **Number_Of_Rows_Output**  
 Anzahl der durch die Abfrage ausgegebenen Zeilen. Dies ist eine Haupteigenschaft. Der Wert ist " **bigint".**  
  
 **Internal_Filter_Efficiency**  
 Wenn O die Anzahl der ausgegebenen Zeilen ist, gibt dies S/O als Prozentsatz zurück. Dies ist eine Haupteigenschaft. Der Wert ist " **float".**  
  
 **Primary_Filter_Efficiency**  
 Wenn P Zeilen durch den primären Filter ausgewählt werden und O die Anzahl der ausgegebenen Zeilen ist, wird dieser returnso/P als Prozentsatz angegeben. Je höher die Effizienz des primären Filters, desto weniger falsch positive Meldungen muss der sekundäre Filter verarbeiten. Dies ist eine Haupteigenschaft. Der Wert ist " **float".**  
  
## <a name="permissions"></a>Berechtigungen  
 Der Benutzer muss ein Mitglied der Datenbankrolle **public** sein. Erfordert die READ ACCESS-Berechtigung für den Server und das Objekt. Dies gilt für alle gespeicherten Prozeduren für Räumlichkeitsindizes.  
  
## <a name="remarks"></a>Hinweise  
 Eigenschaften, die NULL-Werte enthalten sind, sind nicht in der zurückgegebenen Menge enthalten.  
  
## <a name="examples"></a>Beispiele  
 Beispiele finden Sie in den folgenden Themen:  
  
-   [sp_help_spatial_geometry_index &#40;(Transact-SQL)&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)  
  
-   [sp_help_spatial_geometry_index_xml &#40;(Transact-SQL)&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-xml-transact-sql.md)  
  
-   [sp_help_spatial_geography_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)  
  
-   [sp_help_spatial_geography_index_xml &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-xml-transact-sql.md)  
  
## <a name="requirements"></a>Anforderungen  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren &#40;für räumliche Indizes Transact-SQL&#41;](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geometry_index &#40;(Transact-SQL)&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)   
 [Übersicht über räumliche Indizes](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [XQuery-Grundlagen](../../xquery/xquery-basics.md)   
 [XQuery-Sprachreferenz &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md)  
  
  
