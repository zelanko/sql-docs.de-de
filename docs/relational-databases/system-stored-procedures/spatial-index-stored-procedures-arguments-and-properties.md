---
title: Argumente und Eigenschaften des räumlichen Indexes gespeicherten Prozeduren | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: ccd9e2be26c8d514e17a4aa03af422cd648fe426
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51666599"
---
# <a name="spatial-index-stored-procedures---arguments-and-properties"></a>Räumlicher Index gespeicherte Prozeduren – Argumente und Eigenschaften
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In diesem Thema sind die Argumente und Eigenschaften gespeicherter Prozeduren für Räumlichkeitsindizes dokumentiert.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
 Die Syntax bestimmter gespeicherter Prozeduren für Räumlichkeitsindizes finden Sie in den folgenden Themen:  
  
-   [Sp_help_spatial_geometry_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)  
  
-   [Sp_help_spatial_geometry_index_xml &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-xml-transact-sql.md)  
  
-   [Sp_help_spatial_geography_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)  
  
-   [Sp_help_spatial_geography_index_xml &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-xml-transact-sql.md)  
  
## <a name="arguments"></a>Argumente  
 [  **@tabname =**] **"***Tabname***"**  
 Der qualifizierte oder nicht qualifizierte Name der Tabelle, für die der Räumlichkeitsindex angegeben wurde.  
  
 Anführungszeichen sind nur dann erforderlich, wenn eine qualifizierte Tabelle angegeben wird. Bei Angabe eines vollqualifizierten Namens, einschließlich eines Datenbanknamens, muss es sich bei dem Datenbanknamen um den Namen der aktuellen Datenbank handeln. *Tabname* ist **Nvarchar**(776) und hat keinen Standardwert.  
  
 [  **@indexname =** ] **"***Indexname***"**  
 Der Name des angegebenen räumlichen Indexes. *Indexname* ist **Sysname** hat keinen Standardwert.  
  
 [  **@verboseoutput =** ] **"***Verboseoutput***"**  
 Der Bereich von Eigenschaftsnamen und Werten, die zurückgegeben werden sollen.  
  
 0 = Haupteigenschaften  
  
 \>0 = alle Eigenschaften  
  
 *Verboseoutput* ist **Tinyint** hat keinen Standardwert.  
  
 [  **@query_sample =** ] **"***Abfragebeispiel***"**  
 Ein repräsentatives Abfragebeispiel, das verwendet werden kann, um die Nützlichkeit des Indexes zu testen. Dabei kann es sich um ein repräsentatives Objekt oder ein Abfragefenster handeln. *Abfragebeispiel* ist **Geometrie** hat keinen Standardwert.  
  
 [  **@xml_output =** ] **"***XML***"**  
 Ein Ausgabeparameter, der das Resultset in einem XML-Fragment zurückgibt. *XML* ist **Xml** hat keinen Standardwert.  
  
## <a name="properties"></a>Eigenschaften  
 Legen Sie **@verboseoutput** = 0, um Kerneigenschaften wie in der folgenden Tabelle gezeigt. **@verboseoutput** > 0, um alle Eigenschaften des räumlichen Indexes zurückzugeben.  
  
 **Base_Table_Rows**  
 Anzahl der Zeilen in der Basistabelle. Wert ist **Bigint**.  
  
 **Spalten Bounding_Box_xmin**  
 X-Minimum-Eigenschaften des räumlichen Index für umgebenden Felds **Geometrie** Typ. Wert dieser Eigenschaft ist NULL für **Geography**Typ. Wert ist **"float"**.  
  
 **Bounding_Box_ymin**  
 Y-Minimum-Eigenschaften des räumlichen Index für umgebenden Felds **Geometrie** Typ. Wert dieser Eigenschaft ist NULL für **Geography** Typ. Wert ist **"float"**.  
  
 **Bounding_Box_xmax**  
 X-Maximum-Eigenschaften des räumlichen Index für umgebenden Felds **Geometrie** Typ. Wert dieser Eigenschaft ist NULL für **Geography** Typ. Wert ist **"float"**.  
  
 **Bounding_Box_ymax**  
 Y-Maximum-Eigenschaften des räumlichen Index für umgebenden Felds **Geometrie** Typ. Wert dieser Eigenschaft ist NULL für **Geography** Typ. Wert ist **"float"**.  
  
 **Grid_Size_Level_1**  
 Ebene 1 die Dichte des Rasters des räumlichen Indexes:  
  
 16 für LOW  
  
 64 für MEDIUM  
  
 256 für HIGH  
  
 Wert ist **Int**.  
  
 **Grid_Size_Level_2**  
 Ebene 2 die Dichte des Rasters des räumlichen Indexes:  
  
 16 für LOW  
  
 64 für MEDIUM  
  
 256 für HIGH  
  
 Wert ist **Int**.  
  
 **Grid_Size_Level_3**  
 Ebene 3 die Dichte des Rasters des räumlichen Indexes:  
  
 16 für LOW  
  
 64 für MEDIUM  
  
 256 für HIGH  
  
 Wert ist **Int**.  
  
 **Grid_Size_Level_4**  
 Rasterdichte der Ebene 4 des Räumlichkeitsindex:  
  
 16 für LOW  
  
 64 für MEDIUM  
  
 256 für HIGH  
  
 Wert ist **Int**.  
  
 **Cells_Per_Object**  
 Anzahl der Zellen pro Objekt (Indexeigenschaft). Wert ist **Int**.  
  
 **Total_Primary_Index_Rows**  
 Anzahl der Zeilen im Index. Wert ist **Bigint**.  
  
 **Total_Primary_Index_Pages**  
 Anzahl der Seiten im Index. Wert ist **Bigint**.  
  
 **Average_Number_Of_Index_Rows_Per_Base_Row**  
 Anzahl der Indexzeilen/Anzahl der Basistabellenzeilen. Wert ist **Bigint**.  
  
 **Total_Number_Of_ObjectCells_In_Level0_For_QuerySample**  
 Gibt an, ob das repräsentative Abfragebeispiel außerhalb des umgebenden Felds liegt die **Geometrie** Index und in der stammzelle (Zelle der Ebene 0). Dies ist entweder 0 (nicht in Zelle der Ebene 0) oder 1. Befindet es sich in der Zelle der Ebene 0, ist der untersuchte Index nicht für das Abfragebeispiel geeignet. Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Total_Number_Of_ObjectCells_In_Level0_In_Index**  
 Anzahl der zelleninstanzen indizierter Objekte, die im Mosaikprozess in Ebene 0 berücksichtigt werden (stammzelle, außerhalb des umgebenden Felds für **Geometrie**). Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 Für **Geometrie** Indizes, das geschieht, wenn das umgebende Feld des Indexes kleiner ist als die Datendomäne ist. Eine hohe Anzahl von Objekten in Ebene 0 möglicherweise sekundäre Filter, wenn das Abfragefenster teilweise aus dem umgebenden fällt Feld und beeinträchtigt die indexleistung (z. B. **Total_Number_Of_ObjectCells_In_Level0_For_QuerySample** 1). Wenn das Abfragefenster innerhalb des umgebenden Felds liegt, kann eine hohe Anzahl an Objekten in Ebene 0 die Leistung des Indexes tatsächlich verbessern.  
  
 NULL und leere Instanzen werden auf Ebene 0 gezählt, wirken sich aber nicht auf die Leistung aus. Ebene 0 hat so viele Zellen wie NULL und leere Instanzen in der Basistabelle. Für **Geography** -Indizes hat Ebene 0 hat so viele Zellen wie NULL und leere Instanzen + 1 Zelle, da das Abfragebeispiel als 1 gezählt wird.  
  
 **Total_Number_Of_ObjectCells_In_Level1_In_Index**  
 Die Anzahl der zelleninstanzen indizierter Objekte, die mit einer Genauigkeit von Ebene 1 im Mosaikprozess berücksichtigt werden. Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Total_Number_Of_ObjectCells_In_Level2_In_Index**  
 Die Anzahl der zelleninstanzen indizierter Objekte, die mit einer Genauigkeit von Ebene 2 im Mosaikprozess berücksichtigt werden. Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Total_Number_Of_ObjectCells_In_Level3_In_Index**  
 Die Anzahl der zelleninstanzen indizierter Objekte, die mit einer Genauigkeit von Ebene 3 im Mosaikprozess berücksichtigt werden. Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Total_Number_Of_ObjectCells_In_Level4_In_Index**  
 Anzahl der Zelleninstanzen indizierter Objekte, die im Mosaikprozess mit dem Genauigkeitsgrad 4 berücksichtigt werden. Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Total_Number_Of_interior_ObjectCells_In_Level1_In_Index**  
 Anzahl der Zellen, die vollständig von einem Objekt auf mosaikebene 1 abgedeckt werden und daher inneren des Objekts. (Cell_attributevalue ist 2.) Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Total_Number_Of_interior_ObjectCells_In_Level2_In_Index**  
 Anzahl der Zellen, die vollständig von einem Objekt auf mosaikebene 2 abgedeckt werden und daher inneren des Objekts. (Cell_attribute-Wert ist 2.) Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Total_Number_Of_interior_ObjectCells_In_Level3_In_Index**  
 Anzahl der Zellen, die von einem Objekt auf mosaikebene 3 vollständig abgedeckt werden und daher inneren des Objekts. (Cell_attribute-Wert ist 2.) Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Total_Number_Of_interior_ObjectCells_In_Level4_In_Index**  
 Anzahl der Zellen, die vollständig von einem Objekt auf Mosaikebene 4 abgedeckt werden und daher im Inneren des Objekts liegen. (Cell_attribute-Wert ist 2.) Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level1_In_Index**  
 Die Anzahl der Zellen, die von einem Objekt auf mosaikebene 1 eine Schnittmenge gebildet werden. (Cell_attribute-Wert ist 1.) Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level2_In_Index**  
 Die Anzahl der Zellen, die von einem Objekt auf mosaikebene 2 eine Schnittmenge gebildet werden. (Cell_attribute-Wert ist 1.) Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level3_In_Index**  
 Die Anzahl der Zellen, die von einem Objekt auf mosaikebene 3 eine Schnittmenge gebildet werden. (Cell_attribute-Wert ist 1.) Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level4_In_Index**  
 Anzahl der Zellen, die von einem Objekt auf Mosaikebene 4 geschnitten werden. (Cell_attribute-Wert ist 1.) Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level0_For_QuerySample**  
 Gibt an, ob sich das Abfragebeispiel in Stammzelle 0 außerhalb des umgebenden Felds befindet, dieses aber berührt. Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
> [!NOTE]  
>  Diese Informationen sind nur hilfreich, um zu ermitteln, ob Objekte vorhanden sind, die nur knapp neben dem umgebenden Feld liegen.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level0_In_Index**  
 Anzahl der Objekte in Ebene 0, die das umgebende Feld berühren. (Cell_attribute-Wert ist 0.)  Wert ist **Bigint**.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level1_In_Index**  
 Die Anzahl der objektzellen, die eine rasterzellenbegrenzung auf mosaikebene 1 zu berühren. (Cell_attribute-Wert ist 0.) Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level2_In_Index**  
 Die Anzahl der objektzellen, die eine rasterzellenbegrenzung auf mosaikebene 2 zu berühren. (Cell_attribute-Wert ist 0.) Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level3_In_Index**  
 Die Anzahl der objektzellen, die eine rasterzellenbegrenzung auf mosaikebene 3 zu berühren. (Cell_attribute-Wert ist 0.) Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level4_In_Index**  
 Anzahl der Objektzellen, die eine Rasterzellenbegrenzung auf Mosaikebene 4 berühren. (Cell_attribute-Wert ist 0.) Dies ist eine Haupteigenschaft. Wert ist **Bigint**.  
  
 **Interior_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**  
 Prozentsatz des Gesamtbereichs (Summe der Blattzellen) des Rasters, der Blattzellen enthält, die durch ein Objekt abgedeckt werden.  
  
 Beispiel: Ein Objekt wird dem Mosaikprozess unterzogen und in zehn Zellen auf vier verschiedenen Rasterebenen zerlegt, die einen Bereich abdecken, der insgesamt 100 Blattzellen entspricht. Angenommen, es gibt drei innere Zellen, die vollständig durch das Objekt abgedeckt werden. Der durch die drei inneren Zellen abgedeckte Bereich entspricht 42 Blattzellen. Somit liegt der Prozentsatz an abgedecktem Bereich bei 42 Prozent. Dies ist ein gutes Maß dafür, wie gut die Objekte im Index aufgeteilt sind.  
  
 Wert ist **"float"**.  
  
 **Intersecting_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**  
 Identisch mit **Interior_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**, außer dass diese teilweise abgedeckte Zellen handelt. Wert ist **"float"**.  
  
 **Border_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**  
 Identisch mit **Interior_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage** mit dem Unterschied, dass rahmenzellen handelt. Wert ist **"float"**.  
  
 **Average_Cells_Per_Object_Normalized_To_Leaf_Grid**  
 Durchschnittliche Anzahl der Zellen pro Objekt, die auf das Blattraster normalisiert sind. Damit erhalten wir einen Anhaltspunkt zur räumlichen Größe des Objekts oder zur Größe der Objekte. Wert ist **"float"**.  
  
 **Average_Objects_PerLeaf_GridCell**  
 Geringe Dichte des Index. Durchschnittliche Anzahl der Objekte pro Blattzelle. Wert ist **"float"**.  
  
 **Number_Of_SRIDs_Found**  
 Anzahl der eindeutigen SRIDs im Index und in der Spalte. Wert ist **Int**.  
  
 Da eine Spalte mehrere SRIDs enthalten kann und sich Objekte mit unterschiedlichen SRIDs niemals schneiden, gibt die Anzahl der SRIDs die Selektivität des Indexes an.  
  
 **Width_Of_Cell_In_Level1**  
 Breiteneigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird durch den Index bereitgestellt, und abhängig vom SRID der indizierten Daten. Wert ist **"float"**.  
  
 **Width_Of_Cell_In_Level2**  
 Breiteneigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird durch den Index bereitgestellt, und abhängig vom SRID der indizierten Daten. Wert ist **"float"**.  
  
 **Width_Of_Cell_In_Level3**  
 Breiteneigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird durch den Index bereitgestellt, und abhängig vom SRID der indizierten Daten. Wert ist **"float"**.  
  
 **Width_Of_Cell_In_Level4**  
 Breiteneigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird durch den Index vorgegeben und hängt von der SRID der indizierten Daten ab. Wert ist **"float"**.  
  
 **Height_Of_Cell_In_Level1**  
 Höheneigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird durch den Index bereitgestellt, und abhängig vom SRID der indizierten Daten. Wert ist **"float"**.  
  
 **Height_Of_Cell_In_Level2**  
 Höheneigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird durch den Index bereitgestellt, und abhängig vom SRID der indizierten Daten. Wert ist **"float"**.  
  
 **Height_Of_Cell_In_Level3**  
 Höheneigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird durch den Index bereitgestellt, und abhängig vom SRID der indizierten Daten. Wert ist **"float"**.  
  
 **Height_Of_Cell_In_Level4**  
 Höheneigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird durch den Index bereitgestellt, und abhängig vom SRID der indizierten Daten. Wert ist **"float"**.  
  
 **Area_Of_Cell_In_Level1**  
 Bereichseigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird durch den Index bereitgestellt, und abhängig vom SRID der indizierten Daten. Wert ist **"float"**.  
  
 **Area_Of_Cell_In_Level2**  
 Bereichseigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird durch den Index bereitgestellt, und abhängig vom SRID der indizierten Daten. Wert ist **"float"**.  
  
 **Area_Of_Cell_In_Level3**  
 Bereichseigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird durch den Index bereitgestellt, und abhängig vom SRID der indizierten Daten. Wert ist **"float"**.  
  
 **Area_Of_Cell_In_Level4**  
 Bereichseigenschaft der Zelle im Indizierungsraster. Die Maßeinheit wird durch den Index bereitgestellt, und abhängig vom SRID der indizierten Daten. Wert ist **"float"**.  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level1**  
 Der Prozentsatz der Abdeckung des umgebenden Felds durch eine Zelle der Ebene 1. Wert ist **"float"**.  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level2**  
 Der Prozentsatz der Abdeckung des umgebenden Felds durch eine Zelle der Ebene 2. Wert ist **"float"**.  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level3**  
 Der Prozentsatz der Abdeckung des umgebenden Felds durch eine Zelle auf Ebene 3. Wert ist **"float"**.  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level4**  
 Der Prozentsatz der Abdeckung des umgebenden Felds durch eine Zelle der Ebene 4. Wert ist **"float"**.  
  
 **Number_Of_Rows_Selected_By_Primary_Filter**  
 Anzahl der durch den primären Filter ausgewählten Zeilen. Dies ist eine Haupteigenschaft. Wert ist **Bigint.**  
  
 **Number_Of_Rows_Selected_By_Internal_Filter**  
 Anzahl der durch den internen Filter ausgewählten Zeilen. Der sekundäre Filter wird für diese Zeilen nicht aufgerufen. Dies ist eine Haupteigenschaft. Wert ist **Bigint.**  
  
 Die zurückgegebene Anzahl gilt nur für **STintersects**.  
  
 **Number_Of_Times_Secondary_Filter_Is_Called**  
 Anzahl der Aufrufe des sekundären Filters. Dies ist eine Haupteigenschaft. Wert ist **Bigint.**  
  
 **Percentage_Of_Rows_NotSelected_By_Primary_Filter**  
 Wenn N Zeilen in der Basistabelle enthalten sind und P durch den primären Filter ausgewählt werden, gibt dies (N-P)/N als Prozentsatz zurück. Dies ist eine Haupteigenschaft. Wert ist **"float".**  
  
 **Percentage_Of_Primary_Filter_Rows_Selected_By_internal_Filter**  
 Wenn P Zeilen durch den primären Filter und S Zeilen durch den internen Filter ausgewählt werden, gibt dies S/P als Prozentsatz zurück. Je höher der Prozentsatz, desto besser kann der Index den leistungsintensiveren sekundären Filter vermeiden. Dies ist eine Haupteigenschaft. Wert ist **"float".**  
  
 **Number_Of_Rows_Output**  
 Anzahl der durch die Abfrage ausgegebenen Zeilen. Dies ist eine Haupteigenschaft. Wert ist **Bigint.**  
  
 **Internal_Filter_Efficiency**  
 Wenn O die Anzahl der ausgegebenen Zeilen ist, gibt dies S/O als Prozentsatz zurück. Dies ist eine Haupteigenschaft. Wert ist **"float".**  
  
 **Primary_Filter_Efficiency**  
 Wenn P Zeilen durch den primären Filter und O ausgewählt sind ist die Anzahl der Zeilen, die für die Ausgabe dieser ReturnsO/P als Prozentsatz. Je höher die Effizienz des primären Filters, desto weniger falsch positive Meldungen muss der sekundäre Filter verarbeiten. Dies ist eine Haupteigenschaft. Wert ist **"float".**  
  
## <a name="permissions"></a>Berechtigungen  
 Der Benutzer muss ein Mitglied der Datenbankrolle **public** sein. Erfordert die READ ACCESS-Berechtigung für den Server und das Objekt. Dies gilt für alle gespeicherten Prozeduren für Räumlichkeitsindizes.  
  
## <a name="remarks"></a>Hinweise  
 Eigenschaften, die NULL-Werte enthalten sind, sind nicht in der zurückgegebenen Menge enthalten.  
  
## <a name="examples"></a>Beispiele  
 Beispiele finden Sie in den folgenden Themen:  
  
-   [Sp_help_spatial_geometry_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)  
  
-   [Sp_help_spatial_geometry_index_xml &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-xml-transact-sql.md)  
  
-   [Sp_help_spatial_geography_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)  
  
-   [Sp_help_spatial_geography_index_xml &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-xml-transact-sql.md)  
  
## <a name="requirements"></a>Anforderungen  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren für Räumlichkeitsindizes &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [Sp_help_spatial_geometry_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)   
 [Übersicht über räumliche Indizes](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [XQuery-Grundlagen](../../xquery/xquery-basics.md)   
 [XQuery-Sprachreferenz &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md)  
  
  
