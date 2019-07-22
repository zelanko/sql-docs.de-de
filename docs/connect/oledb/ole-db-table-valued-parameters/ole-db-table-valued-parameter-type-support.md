---
title: OLE DB-Typunterstützung für Tabellenwertparameter | Microsoft-Dokumentation
description: OLE DB-Typunterstützung für Tabellenwertparameter
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
author: pmasl
ms.author: pelopes
ms.openlocfilehash: abff9abb82ad0ff54d9b1126541b98babbd6bd76
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015286"
---
# <a name="ole-db-table-valued-parameter-type-support"></a>OLE DB-Typunterstützung für Tabellenwertparameter
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  In diesem Artikel wird die OLE DB-Typunterstützung für Tabellenwertparameter beschrieben.  
  
## <a name="table-valued-parameter-rowset-object"></a>Tabellenwertparameter-Rowsetobjekt  
 Sie können ein spezielles Rowsetobjekt für Tabellenwertparameter erstellen. Sie erstellen das Tabellenwert Parameter-Rowsetobjekt mithilfe von ITableDefinitionWithConstraints:: kreatetablewitheinschränkungs-oder IOpenRowset:: OpenRowset. Legen Sie hierzu das *eKind*-Element des *pTableID*-Parameters auf DBKIND_GUID_NAME fest, und geben Sie für das *guid*-Element CLSID_ROWSET_INMEMORY an. Der Servertyp Name für den Tabellenwert Parameter muss im *pwszName* -Member von *pTableID* angegeben werden, wenn IOpenRowset:: OPENROWSET verwendet wird. Das Tabellenwert Parameter-Rowsetobjekt verhält sich wie ein regulärer OLE DB Treiber für SQL Server-Objekt.  
  
```  
const GUID CLSID_ROWSET_TVP =   
{0xc7ef28d5, 0x7bee, 0x443f, {0x86, 0xda, 0xe3, 0x98, 0x4f, 0xcd, 0x4d, 0xf9}};  
  
CoType RowsetTVP  
{  
[mandatory] interface IAccessor;  
[mandatory] interface IColumnsInfo;  
[mandatory] interface IConvertType;  
[mandatory] interface IRowset;  
[mandatory] interface IRowsetInfo;  
[optional]  interface IColumnsRowset;  
[optional]  interface IRowsetChange;  
[optional]  interface ISupportErrorInfo;  
};  
```  
  
## <a name="dbtypetable"></a>DBTYPE_TABLE  
 Der neue Typ DBTYPE_TABLE stellt einen Tabellentyp dar. Dieser Typ gibt Tabellenwertparameter in verschiedenen OLE DB-Schnittstellen an, wo ein DBTYPE erforderlich ist.  
  
```  
#define DBTYPE_TABLE (143)  
```  
  
 DBTYPE_TABLE hat das gleiche Format wie DBTYPE_IUNKNOWN. Es ist ein Zeiger auf ein Objekt im Datenpuffer. Um die Bindungen vollständig anzugeben, füllt der Consumer den DBOBJECT-Puffer, wobei *iid* auf eine der Schnittstellen des Rowsetobjekts (IID_IRowset) festgelegt wird. Wenn in den Bindungen die Angabe von DBOBJECT fehlt, wird IID_IRowset angenommen.  
  
 Konvertierungen zu und von DBTYPE_TABLE für andere Typen werden nicht unterstützt. Außer bei einer Konvertierung von DBTYPE_TABLE zu DBTYPE_TABLE gibt IConvertType::CanConvert bei einer nicht unterstützten Konvertierung für jede Anforderung S_FALSE zurück. Hierbei wird die Angabe von DBCONVERTFLAGS_PARAMETER für das Command-Objekt angenommen.  
  
## <a name="methods"></a>Methoden  
 Weitere Informationen zu OLE DB Methoden, die Tabellenwert Parameter unterstützen, finden Sie [unter Unterstützung &#40;&#41;von OLE DB Tabellenwert Parameter-Typen](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md).  
  
## <a name="properties"></a>Eigenschaften  
 Informationen zu OLE DB Eigenschaften, die Tabellenwert Parameter unterstützen, finden Sie [unter Unterstützung &#40;&#41;von OLE DB Tabellenwert Parameter-Typen](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenwertparameter &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
