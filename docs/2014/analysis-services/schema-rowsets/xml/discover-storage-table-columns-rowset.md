---
title: DISCOVER_STORAGE_TABLE_COLUMNS-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 24abb88e-33a9-4ae2-829d-cdef0ff22ec1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 240230784860e9484ebc03ba6740eaf5d56387fa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089070"
---
# <a name="discoverstoragetablecolumns-rowset"></a>DISCOVER_STORAGE_TABLE_COLUMNS-Rowset
  Stellt Informationen zu Speichertabellen auf Spaltenebene bereit, die von einer im SharePoint- oder tabellarischen Modus ausgeführten Analysis Services-Datenbank verwendet werden.  
  
 **Gilt für:** tabellarische Modelle  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_STORAGE_TABLE_COLUMNS` Rowset enthält die folgenden Spalten.  
  
|**Spaltenname**|**Typindikator**|**Einschränkung**|**Beschreibung**|  
|---------------------|------------------------|---------------------|---------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Benutzerkontensteuerung|Gibt den Namen der Datenbank an, die die Tabellen enthält. Bei Auslassung wird die aktuelle Datenbank verwendet.<br /><br /> Die `DISCOVER_STORAGE_TABLE_COLUMNS` Rowset kann mithilfe dieser Spalte eingeschränkt werden.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Benutzerkontensteuerung|Gibt den Cube oder das Modell an, das die Tabellen enthält.<br /><br /> Die `DISCOVER_STORAGE_TABLES` Rowset kann mithilfe dieser Spalte eingeschränkt werden.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Benutzerkontensteuerung|Der Name der Measuregruppe.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Der Name der Dimension.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`||Der Name des Attributs.|  
|`TABLE_ID`|`DBTYPE_WSTR`||Die ID der Tabelle.|  
|`COLUMN_ID`|`DBTYPE_ WSTR`||Die ID der Spalte. Die Spalten-ID ist für die xVelocity-Engine für Datenanalyse im Arbeitsspeicher (VertiPaq) intern und wird nur zu Informationszwecken verwendet.|  
|`COLUMN_TYPE`|`DBTYPE_WSTR`||Der Typ der Spalte. Der Spaltentyp ist für die xVelocity-Engine für Datenanalyse im Arbeitsspeicher (VertiPaq) intern und wird nur zu Informationszwecken verwendet.<br /><br /> -BASIC_DATA<br />-HIERARCHY_DATAID_TO_POSITION<br />-HIERARCHY_POSITION_TO_DATAID<br />-DIE BEZIEHUNG|  
|`COLUMN_ENCODING`|`DBTYPE_UI8`||Eine ganze Zahl, die den für Spaltendaten verwendeten Codierungstyp darstellt.<br /><br /> -   **0**verwendet mit `COLUMN_TYPE`: HIERARCHY_DATAID_TO_POSITION, HIERARCHY_POSITION_TO_DATAID, Beziehung<br />-   **1**verwendet mit `COLUMN_TYPE`: BASIC_DATA<br />-   **2**verwendet mit `COLUMN_TYPE`: BASIC_DATA|  
|`DATATYPE`|`DBTYPE_WSTR`||Der Datentyp der Spalte. verfügt über folgende Werte möglich:<br /><br /> -DBTYPE_BOOL<br />-DBTYPE_CY<br />-DBTYPE_DATE<br />-DBTYPE_I4<br />-DBTYPE_I8<br />-DBTYPE_R8<br />-DBTYPE_WSTR<br />-N/V|  
|`ISKEY`|`DBTYPE_BOOL`||`True`, falls die Spalte als Primär- oder Fremdschlüssel verwendet wird; andernfalls `false`.|  
|`ISUNIQUE`|`DBTYPE_BOOL`||`True` Wenn die Werte in der Spalte eindeutig sind; andernfalls `false`.|  
|`ISNULLABLE`|`DBTYPE_BOOL`||`True`, falls die Spalte auf NULL festgelegt werden kann; andernfalls `false`.|  
|`ISROWNUMBER`|`DBTYPE_BOOL`||`True`, falls die Spalte eine Zeilennummernspalte ist. Zeilennummernspalten zur internen Verwendung durch die xVelocity-Engine für Datenanalyse im Arbeitsspeicher.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Verwenden von ADOMD.NET zum Zurückgeben des Rowsets  
 Wenn Sie Metadaten mithilfe von ADOMD.NET und des Schemarowsets abrufen, können Sie entweder die GUID verwenden oder eine Referenz für ein Schemarowsetobjekt in der GetSchemaDataSet-Methode herstellen. Weitere Informationen finden Sie unter [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Die folgende Tabelle enthält die GUID und die Zeichenfolgenwerte, die dieses Rowset identifizieren.  
  
|Argument|value|  
|--------------|-----------|  
|GUID|a07ccd44-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|StorageTableColumns|  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel gibt das Resultset mithilfe einer DMV-Abfrage zurück.  
  
```  
SELECT *  
FROM $System.DISCOVER_STORAGE_TABLE_COLUMNS  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Schemarowsets](../analysis-services-schema-rowsets.md)  
  
  
