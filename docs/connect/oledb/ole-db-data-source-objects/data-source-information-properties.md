---
title: Eigenschaften von Datenquelleninformationen | Microsoft-Dokumentation
description: Eigenschaften von Datenquelleninformationen
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [OLE DB Driver for SQL Server]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: ba9fa21f0c22c342922946a43124216a25ba09ef
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68016034"
---
# <a name="data-source-information-properties"></a>Eigenschaften für Datenquelleninformationen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Im anbieterspezifischen Eigenschaftensatz DBPROPSET_SQLSERVERDATASOURCEINFO definiert der OLE DB-Treiber für SQL Server die folgenden Eigenschaften für Datenquelleninformationen.  
  
|Eigenschafts-ID|Beschreibung|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|Typ: VT_BOOL<br /><br /> R/W: Lesen<br /><br /> Standardwert: VARIANT_TRUE<br /><br /> Beschreibung: wird verwendet, um zu ermitteln, ob Spaltensortierung unterstützt wird<br /><br /> VARIANT_TRUE: Spaltenebenensortierung wird unterstützt<br /><br /> VARIANT_FALSE: Spaltenebenensortierung wird nicht unterstützt|  
|SSPROP_UNICODELCID|Typ: VT_I4 R/W: Lesen<br /><br /> Beschreibung: Unicode-ID des Gebietsschemas<br /><br /> Dabei handelt es sich um das für die Unicode-Datensortierung verwendete Gebietsschema.|  
|SSPROP_UNICODECOMPARISONSTYLE|Typ: VT_I4 R/W: Lesen<br /><br /> Beschreibung: Stil des Unicodevergleichs<br /><br /> Dabei handelt es sich um die für die Unicode-Datensortierung verwendeten Sortieroptionen.|  
  
 Im anbieterspezifischen Eigenschaftensatz DBPROPSET_SQLSERVERSTREAM definiert der OLE DB-Treiber für SQL Server die folgende zusätzliche Eigenschaft.  
  
|Eigenschafts-ID|BESCHREIBUNG|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|Typ: VT_BSTR R/W: Lesen/Schreiben<br /><br /> Beschreibung: FOR XML-Abfragen geben möglicherweise keine wohlgeformten Dokumente zurück. Wenn diese Eigenschaft angegeben ist, wird das Ergebnis einer „select … for XML“-Abfrage von einem Stammtag umschlossen, das von dieser Eigenschaft bereitgestellt wird, um ein wohlgeformtes XML-Dokument zurückzugeben. Wenn die Abfrage in einem Browser ausgeführt wird, führt das möglicherweise dazu, dass der Browser beim Laden des Ergebnisses Parserfehler anzeigt. Um den Fehler zu vermeiden, unterstützt SQL ISAPI das Schlüsselwort ROOT. Dieses Schlüsselwort wird der SSPROP_STREAM_XMLROOT-Eigenschaft zugeordnet.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenquellenobjekte &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
