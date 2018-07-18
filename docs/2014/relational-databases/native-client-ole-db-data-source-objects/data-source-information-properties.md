---
title: Datenquelleneigenschaften Informationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 7fd80e47-5bd9-41e2-a3d3-091a7c8c5f2b
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8ac3906946e7f732d9f7ddb92989ceaf79c5225c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410021"
---
# <a name="data-source-information-properties"></a>Eigenschaften für Datenquelleninformationen
  Im anbieterspezifischen Eigenschaftensatz DBPROPSET_SQLSERVERDATASOURCEINFO definiert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter die folgenden Eigenschaften für Datenquelleninformationen.  
  
|Eigenschafts-ID|Description|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|Typ: VT_BOOL<br /><br /> R/W: Lesen<br /><br /> Standard: VARIANT_TRUE<br /><br /> Beschreibung: Wird verwendet, um zu ermitteln, ob Spaltensortierung unterstützt wird.<br /><br /> VARIANT_TRUE: Spaltenebenensortierung wird unterstützt.<br /><br /> VARIANT_FALSE: Spaltenebenensortierung wird nicht unterstützt.|  
|SSPROP_UNICODELCID|Typ: VT_I4 R/W: Lesen<br /><br /> Beschreibung: Unicode-Gebietsschema-ID<br /><br /> Dabei handelt es sich um das für die Unicode-Datensortierung verwendete Gebietsschema.|  
|SSPROP_UNICODECOMPARISONSTYLE|Typ: VT_I4 R/W: Lesen<br /><br /> Beschreibung: Unicode-Vergleichsart<br /><br /> Dabei handelt es sich um die für die Unicode-Datensortierung verwendeten Sortieroptionen.|  
  
 Im anbieterspezifischen Eigenschaftensatz DBPROPSET_SQLSERVERSTREAM definiert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter die folgende zusätzliche Eigenschaft.  
  
|Eigenschafts-ID|Description|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|Typ: VT_BSTR R/W: Lesen/Schreiben<br /><br /> Beschreibung: Das Ergebnis einer FOR XML-Abfrage ist möglicherweise kein wohlgeformtes Dokument. Diese Eigenschaft wird angegeben, das Ergebnis einer ' auswählen... für die XML-' Abfrage wird das Stamm-Tag, die von dieser Eigenschaft auf ein wohlgeformtes XML-Dokument zurückgeben bereitgestellt umschlossen. Wenn die Abfrage in einem Browser ausgeführt wird, führt das möglicherweise dazu, dass der Browser beim Laden des Ergebnisses Parserfehler anzeigt. Um den Fehler zu vermeiden, unterstützt SQL ISAPI das Schlüsselwort ROOT. Dieses Schlüsselwort wird der SSPROP_STREAM_XMLROOT-Eigenschaft zugeordnet.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellenobjekte &#40;OLE-DB&#41;](data-source-objects-ole-db.md)  
  
  
