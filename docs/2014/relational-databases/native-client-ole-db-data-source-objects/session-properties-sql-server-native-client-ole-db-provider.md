---
title: Eigenschaften von leistungssitzungen | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- SQL Server Native Client OLE DB provider, sessions
ms.assetid: 2498fbad-b3db-4bea-8fc6-fef5317d3eba
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 310c69d13582a52800f7b5bb26f65a23c806fb24
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048046"
---
# <a name="session-properties"></a>Sitzungseigenschaften
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter interpretiert OLE DB-Sitzungseigenschaften wie folgt.  
  
|Eigenschafts-ID|Description|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt alle Autocommit Isolationsstufen von Transaktionen mit Ausnahme der chaosstufe DBPROPVAL_TI_CHAOS.|  
  
 Im anbieterspezifischen Eigenschaftensatz DBPROPSET_SQLSERVERSESSION, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter definiert die folgende zusätzliche Sitzungseigenschaft.  
  
|Eigenschafts-ID|Description|  
|-----------------|-----------------|  
|SSPROP_QUOTEDCATALOGNAMES|Typ: VT_BOOL<br /><br /> R/w: Lesen/Schreiben<br /><br /> Standard: VARIANT_FALSE<br /><br /> Beschreibung: In CATALOG-Einschränkung zugelassene Bezeichner in Anführungszeichen.<br /><br /> VARIANT_TRUE: Bezeichner in Anführungszeichen werden für eine CATALOG-Einschränkung für die Schemarowsets erkannt, die Unterstützung für verteilte Abfragen bieten.<br /><br /> VARIANT_FALSE: Bezeichner in Anführungszeichen werden nicht für eine CATALOG-Einschränkung für die Schemarowsets erkannt, die Unterstützung für verteilte Abfragen bieten.<br /><br /> Weitere Informationen zu Schemarowsets dar, die Unterstützung für verteilte Abfragen bieten, finden Sie unter [Unterstützung von verteilten Abfragen in Schemarowsets](../native-client/ole-db/schema-rowsets-distributed-query-support.md).|  
|SSPROP_ALLOWNATIVEVARIANT|Typ: VT_BOOL<br /><br /> R/W: Lesen/Schreiben<br /><br /> Standard: VARIANT_FALSE<br /><br /> Beschreibung: Bestimmt, ob die Daten als DBTYPE_VARIANT oder DBTYPE_SQLVARIANT abgerufen werden.<br /><br /> VARIANT_TRUE: Der Spaltentyp wird als DBTYPE_SQLVARIANT zurückgegeben. In diesem Fall enthält der Puffer die SSVARIANT-Struktur.<br /><br /> VARIANT_FALSE: Der Spaltentyp wird als DBTYPE_VARIANT zurückgegeben und der Puffer enthält die VARIANT-Struktur.|  
|SSPROP_ASYNCH_BULKCOPY|Zur Verwendung des asynchronen Modus legen Sie die anbieterspezifische Sitzungseigenschaft SSPROP_ASYNCH_BULKCOPY vor dem Aufrufen der BCPExec-Methode auf VARIANT_TRUE fest. Diese Eigenschaft ist im DBPROPSET_SQLSERVERSESSION-Eigenschaftensatz verfügbar.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellenobjekte &#40;OLE DB&#41;](data-source-objects-ole-db.md)  
  
  