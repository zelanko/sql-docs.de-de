---
title: Datenquelleneigenschaften Informationen | Microsoft-Dokumentation
description: Eigenschaften von Datenquelleninformationen
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 0fd9afc87acfb4c39e406ea3deb0b5e9bd7e82d0
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2018
ms.locfileid: "39108132"
---
# <a name="data-source-information-properties"></a>Eigenschaften für Datenquelleninformationen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Im anbieterspezifischen Eigenschaftensatz DBPROPSET_SQLSERVERDATASOURCEINFO definiert der OLE DB-Treiber für SQL Server die folgenden Eigenschaften für Datenquelleninformationen.  
  
|Eigenschafts-ID|und Beschreibung|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|Typ: VT_BOOL<br /><br /> R/W: Lesen<br /><br /> Standard: VARIANT_TRUE<br /><br /> Beschreibung: Wird verwendet, um zu ermitteln, ob Spaltensortierung unterstützt wird.<br /><br /> VARIANT_TRUE: Spaltenebenensortierung wird unterstützt.<br /><br /> VARIANT_FALSE: Spaltenebenensortierung wird nicht unterstützt.|  
|SSPROP_UNICODELCID|Typ: VT_I4 R/W: Lesen<br /><br /> Beschreibung: Unicode-Gebietsschema-ID<br /><br /> Dabei handelt es sich um das für die Unicode-Datensortierung verwendete Gebietsschema.|  
|SSPROP_UNICODECOMPARISONSTYLE|Typ: VT_I4 R/W: Lesen<br /><br /> Beschreibung: Unicode-Vergleichsart<br /><br /> Dabei handelt es sich um die für die Unicode-Datensortierung verwendeten Sortieroptionen.|  
  
 Im anbieterspezifischen Eigenschaftensatz DBPROPSET_SQLSERVERSTREAM definiert der OLE DB-Treiber für SQL Server die folgende zusätzliche Eigenschaft.  
  
|Eigenschafts-ID|und Beschreibung|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|Typ: VT_BSTR R/W: Lesen/Schreiben<br /><br /> Beschreibung: Das Ergebnis einer FOR XML-Abfrage ist möglicherweise kein wohlgeformtes Dokument. Diese Eigenschaft wird angegeben, das Ergebnis einer ' auswählen... für die XML-' Abfrage wird das Stamm-Tag, die von dieser Eigenschaft auf ein wohlgeformtes XML-Dokument zurückgeben bereitgestellt umschlossen. Wenn die Abfrage in einem Browser ausgeführt wird, führt das möglicherweise dazu, dass der Browser beim Laden des Ergebnisses Parserfehler anzeigt. Um den Fehler zu vermeiden, unterstützt SQL ISAPI das Schlüsselwort ROOT. Dieses Schlüsselwort wird der SSPROP_STREAM_XMLROOT-Eigenschaft zugeordnet.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Datenquellenobjekte &#40;OLE-DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
