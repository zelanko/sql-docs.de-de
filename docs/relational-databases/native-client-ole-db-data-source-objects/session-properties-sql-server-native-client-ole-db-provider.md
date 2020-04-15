---
title: Sitzungseigenschaften, SQL Native Client OLE DB
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- SQL Server Native Client OLE DB provider, sessions
ms.assetid: 2498fbad-b3db-4bea-8fc6-fef5317d3eba
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4d4b2bef0bf37b4400ac2cfcb672e43ba4f5abcb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297162"
---
# <a name="session-properties---sql-server-native-client-ole-db-provider"></a>Sitzungseigenschaften – OLE DB-Anbieter von SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-OLE-DB-Anbieter interpretiert ole DB-Sitzungseigenschaften wie folgt.  
  
|Eigenschafts-ID|Beschreibung|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt alle Autocommit-Transaktionsisolationsebenen mit Ausnahme der Chaosebene DBPROPVAL_TI_CHAOS.|  
|||

 Im anbieterspezifischen Eigenschaftensatz DBPROPSET_SQLSERVERSESSION [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definiert der native Client-OLE-DB-Anbieter die folgende zusätzliche Sitzungseigenschaft.  
  
|Eigenschafts-ID|Beschreibung|  
|-----------------|-----------------|  
|SSPROP_QUOTEDCATALOGNAMES|Typ: VT_BOOL<br /><br /> R/W: Lesen/Schreiben<br /><br /> Standard: VARIANT_FALSE<br /><br /> Beschreibung: In CATALOG-Einschränkung zugelassene Bezeichner in Anführungszeichen.<br /><br /> VARIANT_TRUE: Bezeichner in Anführungszeichen werden für eine CATALOG-Einschränkung für die Schemarowsets erkannt, die Unterstützung für verteilte Abfragen bieten.<br /><br /> VARIANT_FALSE: Bezeichner in Anführungszeichen werden nicht für eine CATALOG-Einschränkung für die Schemarowsets erkannt, die Unterstützung für verteilte Abfragen bieten.<br /><br /> Weitere Informationen zu Schemarowsets, die Unterstützung für verteilte Abfragen bieten, finden Sie unter [Unterstützung von verteilten Abfragen in Schemarowsets](../../relational-databases/native-client/ole-db/schema-rowsets-distributed-query-support.md).|  
|SSPROP_ALLOWNATIVEVARIANT|Typ: VT_BOOL<br /><br /> R/W: Lesen/Schreiben<br /><br /> Standard: VARIANT_FALSE<br /><br /> Beschreibung: Bestimmt, ob die Daten als DBTYPE_VARIANT oder DBTYPE_SQLVARIANT abgerufen werden.<br /><br /> VARIANT_TRUE: Der Spaltentyp wird als DBTYPE_SQLVARIANT zurückgegeben. In diesem Fall enthält der Puffer die SSVARIANT-Struktur.<br /><br /> VARIANT_FALSE: Der Spaltentyp wird als DBTYPE_VARIANT zurückgegeben und der Puffer enthält die VARIANT-Struktur.|  
|SSPROP_ASYNCH_BULKCOPY|Zur Verwendung des asynchronen Modus legen Sie die anbieterspezifische Sitzungseigenschaft SSPROP_ASYNCH_BULKCOPY vor dem Aufrufen der BCPExec-Methode auf VARIANT_TRUE fest. Diese Eigenschaft ist im DBPROPSET_SQLSERVERSESSION-Eigenschaftensatz verfügbar.|  
|||

## <a name="see-also"></a>Weitere Informationen  
 [Datenquellenobjekte &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
