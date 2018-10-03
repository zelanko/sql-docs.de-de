---
title: MDSCHEMA_ACTIONS-Rowsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_ACTIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_ACTIONS rowset
ms.assetid: f73081f8-ac51-4286-b46e-2b34e792c3e0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 317ddc9a284df779a44866c0c037310b29f76d02
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140726"
---
# <a name="mdschemaactions-rowset"></a>MDSCHEMA_ACTIONS-Rowset
  Beschreibt die Aktionen, die der Clientanwendung möglicherweise zur Verfügung stehen.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `MDSCHEMA_ACTIONS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Der Name der Datenbank.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Wird nicht unterstützt. Enthält immer `VT_NULL`.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Der Name des Cubes, zu dem diese Aktion gehört.|  
|`ACTION_NAME`|`DBTYPE_WSTR`||Der Name dieser Aktion.|  
|`ACTION_TYPE`|`DBTYPE_I4`||Eine Bitmap, die verwendet wird, um die Triggermethode der Aktion anzugeben. Die Datei Msmd.h definiert die folgenden Bitwertkonstanten für diese Bitmap:<br /><br /> -   `MDACTION_TYPE_URL` (`0x01`)<br />-   `MDACTION_TYPE_HTML` (`0x02`)<br />-   `MDACTION_TYPE_STATEMENT` (`0x04`)<br />-   `MDACTION_TYPE_DATASET` (`0x08`)<br />-   `MDACTION_TYPE_ROWSET` (`0x10`)<br />-   `MDACTION_TYPE_COMMANDLINE` (`0x20`)<br />-   `MDACTION_TYPE_PROPRIETARY` (`0x40`)<br />-   `MDACTION_TYPE_REPORT` (`0x80`)<br />-   `MDACTION_TYPE_DRILLTHROUGH` (`0x100`)|  
|`COORDINATE`|`DBTYPE_WSTR`||Ein MDX-Ausdruck (Multidimensional Expressions), der ein Objekt oder eine Koordinate im mehrdimensionalen Raum angibt, in dem die Aktion ausgeführt wird. Die Clientanwendung ist für die Bereitstellung des Werts für diese Einschränkungsspalte zuständig.<br /><br /> `CORDINATE` muss in das Objekt aufgelöst werden, das in `COORDINATE_TYPE` angegeben ist.|  
|`COORDINATE_TYPE`|`DBTYPE_I4`||Eine Bitmap, die angibt, wie die `COORDINATE`-Einschränkungsspalte interpretiert wird. Die Datei Msmd.h definiert die folgenden Bitwertkonstanten für diese Bitmap:<br /><br /> -   `MDACTION_COORDINATE_CUBE` (`1`)<br />-   `MDACTION_COORDINATE_DIMENSION` (`2`)<br />     Bezieht sich auf die Dimensionshierarchien.<br />-   `MDACTION_COORDINATE_LEVEL` (`3`)<br />-   `MDACTION_COORDINATE_MEMBER` (`4`)<br />-   `MDACTION_COORDINATE_SET` (`5`)<br />-   `MDACTION_COORDINATE_CELL` (`6`)|  
|`ACTION_CAPTION`|`DBTYPE_WSTR`||Der Aktionsname, wenn in der DDL keine Beschriftung und keine Übersetzungen angegeben wurden.<br /><br /> Wenn eine Beschriftung oder Übersetzungen angegeben wurden und `CaptionIsMDX` den Wert False enthält, wird eine der folgenden Zeichenfolgen verwendet:<br /><br /> – Die Übersetzung für die entsprechende Sprache.<br />– Der angegebenen Beschriftung, wenn keine Übersetzung für die angegebene Sprache gefunden wurde.<br />– Der Aktionsname, wenn keine Übersetzung gefunden und der Beschriftung wurde nicht im DDL-Code angegeben.<br /><br /> Wenn eine Beschriftung oder Übersetzungen angegeben wurden und `CaptionIsMDX` den Wert True enthält, die Zeichenfolge, die aus der Suche nach der entsprechenden Übersetzung für die angegebene Sprache oder die in der DDL-Beschriftung angegebene Übersetzung und die Berechnung der Formel zur Erstellung der Zeichenfolge resultiert.<br /><br /> Wenn die Aktion im MDX-Skript angegeben wurde, gibt es keine Übersetzungen und die Beschriftung wird stets als MDX-Ausdruck behandelt.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine benutzerfreundliche Beschreibung der Aktion.|  
|`CONTENT`|`DBTYPE_WSTR`||Der Ausdruck oder Inhalt der Aktion, die ausgeführt werden soll.|  
|`APPLICATION`|`DBTYPE_WSTR`||Der Name der Anwendung, die zur Ausführung der Aktion verwendet werden soll.|  
|`INVOCATION`|`DBTYPE_I4`||Informationen darüber, wie die Aktion aufgerufen werden soll:<br /><br /> -   `MDACTION_INVOCATION_INTERACTIVE` (`1`) gibt eine reguläre Aktion, die während des normalen Betriebs verwendet. Dies ist der Standardwert für diese Spalte.<br />-   `MDACTION_INVOCATION_ON_OPEN` (`2`) gibt an, dass die Aktion ausgeführt werden soll, wenn der Cube erstmalig geöffnet wird.<br />-   `MDACTION_INVOCATION_BATCH` (`4`) gibt an, dass die Aktion, als Teil eines Batchvorgangs ausgeführt wird oder [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Aufgabe.<br /><br /> Diese Enumerationswerte sind in der Datei Msmd.h definiert.|  
  
 Das Rowset wird sortiert nach `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `ACTION_NAME`.  
  
> [!NOTE]  
>  Aktionen des Typs `MDACTION_TYPE_PROPRIETARY` müssen einen Wert für die Spalte `APPLICATION` bereitstellen.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `MDSCHEMA_ACTIONS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Optional|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Optional|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Obligatorisch.|  
|`ACTION_NAME`|`DBTYPE_WSTR`|Optional|  
|`ACTION_TYPE`|`DBTYPE_I4`|Optional|  
|`COORDINATE`|`DBTYPE_WSTR`|Obligatorisch.|  
|`COORDINATE_TYPE`|`DBTYPE_I4`|Obligatorisch.|  
|`INVOCATION`|`DBTYPE_I4`|(Optional) Die `INVOCATION`-Einschränkungsspalte wird standardmäßig auf den Wert von `MDACTION_INVOCATION_INTERACTIVE` festgelegt. Verwenden Sie zum Abrufen aller Aktionen den Wert `MDACTION_INVOCATION_ALL` in der `INVOCATION`-Einschränkungsspalte.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Optional) Eine Bitmap mit einem der folgenden gültigen Werte:<br /><br /> -1-CUBE<br />-2-DIMENSION<br /><br /> Die Standardeinschränkung besitzt den Wert 1.|  
  
> [!IMPORTANT]  
>  Die `INVOCATION`-Einschränkungsspalte verfügt über den Standardwert `MDACTION_INVOCATION_INTERACTIVE`. Jedes Schemarowset, das nicht ausdrücklich einen Wert für diese Spalte angibt, enthält nur Zeilen mit diesem Wert. Wenn das Rowset sämtliche Aktionen enthalten soll, verwenden Sie die Konstante `MDACTION_INVOCATION_ALL` in der `INVOCATION`-Einschränkungsspalte.  
  
 Clientanwendungen können mithilfe des OR-Operators mehr als einen `ACTION_TYPE` definieren.  
  
## <a name="remarks"></a>Hinweise  
 In der folgenden Tabelle sind die gültigen `COORDINATE`- und `COORDINATE_TYPE`-Kombinationen aufgeführt.  
  
|COORDINATE-Objekttyp|COORDINATE_TYPE|  
|----------------------------|----------------------|  
|`Cube`|`MDACTION_COORDINATE_CUBE`|  
|`Dimension`|`MDACTION_COORDINATE_DIMENSION`<br /><br /> `MDACTION_COORDINATE_LEVEL`<br /><br /> `MDACTION_COORDINATE_MEMBER`<br /><br /> `MDACTION_COORDINATE_SET`<br /><br /> `MDACTION_COORDINATE_CELL`|  
|`Hierarchy`|`MDACTION_COORDINATE_DIMENSION`|  
|`Level`|`MDACTION_COORDINATE_LEVEL`|  
|`Member`|`MDACTION_COORDINATE_MEMBER`|  
|`Set`|`MDACTION_COORDINATE_SET`|  
|`cell`|`MDACTION_COORDINATE_CELL`|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](ole-db-for-olap-schema-rowsets.md)  
  
  
