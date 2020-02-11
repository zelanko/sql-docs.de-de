---
title: OLE DB-Typunterstützung für Tabellenwertparameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
ms.assetid: 147036a0-260e-4f81-8b3b-89209e023a32
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 69f7994848d02d6e5e0036aaf132e6294f8d5d90
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73761627"
---
# <a name="ole-db-table-valued-parameter-type-support"></a>OLE DB-Typunterstützung für Tabellenwertparameter
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In diesem Thema wird die OLE DB-Typunterstützung für Tabellenwertparameter beschrieben.  
  
## <a name="table-valued-parameter-rowset-object"></a>Tabellenwertparameter-Rowsetobjekt  
 Sie können ein spezielles Rowsetobjekt für Tabellenwertparameter erstellen. Sie erstellen das Tabellenwert Parameter-Rowsetobjekt mithilfe von ITableDefinitionWithConstraints:: kreatetablewitheinschränkungs-oder IOpenRowset:: OpenRowset. Legen Sie hierzu das *eKind*-Element des *pTableID*-Parameters auf DBKIND_GUID_NAME fest, und geben Sie für das *guid*-Element CLSID_ROWSET_INMEMORY an. Der Servertyp Name für den Tabellenwert Parameter muss im *pwszName* -Member von *pTableID* angegeben werden, wenn IOpenRowset:: OPENROWSET verwendet wird. Das Tabellenwertparameter-Rowsetobjekt verhält sich wie ein reguläres Objekt des OLE DB-Anbieters von SQL Server Native Client.  
  
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
  
## <a name="dbtype_table"></a>DBTYPE_TABLE  
 Der neue Typ DBTYPE_TABLE stellt einen Tabellentyp dar. Dieser Typ gibt Tabellenwertparameter in verschiedenen OLE DB-Schnittstellen an, wo ein DBTYPE erforderlich ist.  
  
```  
#define DBTYPE_TABLE (143)  
```  
  
 DBTYPE_TABLE hat das gleiche Format wie DBTYPE_IUNKNOWN. Es ist ein Zeiger auf ein Objekt im Datenpuffer. Um die Bindungen vollständig anzugeben, füllt der Consumer den DBOBJECT-Puffer, wobei *iid* auf eine der Schnittstellen des Rowsetobjekts (IID_IRowset) festgelegt wird. Wenn in den Bindungen die Angabe von DBOBJECT fehlt, wird IID_IRowset angenommen.  
  
 Konvertierungen zu und von DBTYPE_TABLE für andere Typen werden nicht unterstützt. Außer bei einer Konvertierung von DBTYPE_TABLE zu DBTYPE_TABLE gibt IConvertType::CanConvert bei einer nicht unterstützten Konvertierung für jede Anforderung S_FALSE zurück. Hierbei wird die Angabe von DBCONVERTFLAGS_PARAMETER für das Command-Objekt angenommen.  
  
## <a name="methods"></a>Methoden  
 Informationen zu OLE DB Methoden, die Tabellenwert Parameter unterstützen, finden Sie [unter OLE DB Tabellenwert Parameter-Typunterstützung &#40;Methoden&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md).  
  
## <a name="properties"></a>Eigenschaften  
 Informationen zu OLE DB Eigenschaften, die Tabellenwert Parameter unterstützen, finden Sie [unter OLE DB Tabellenwert Parameter-Typunterstützung &#40;Eigenschaften&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenwertparameter &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
