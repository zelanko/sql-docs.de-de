---
title: OLE DB-Typunterstützung für Tabellenwertparameter (Methoden) | Microsoft-Dokumentation
description: OLE DB-Unterstützung von Tabellenwertparameter-Typen (Methoden)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (methods)
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: ae8245e57b35c644491f8d2e5332ab571996aed0
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2018
ms.locfileid: "39105516"
---
# <a name="ole-db-table-valued-parameter-type-support-methods"></a>OLE DB-Unterstützung von Tabellenwertparameter-Typen (Methoden)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die folgenden Standard-OLE DB-Methoden unterstützen Tabellenwertparameter:  
  
|Methode|Tabellenwertparameter-Unterstützung|  
|------------|-------------------------------------|  
|ITableDefinitionWithConstraints::CreateTableWithConstraints|Wird verwendet, wenn Sie den Typ des Tabellenwertparameters kennen und ein Tabellenwertparameter-Rowsetobjekt anhand der Typinformation instanziieren möchten.<br /><br /> Weitere Informationen finden Sie unter "Statischen Szenario" in [Table-Valued Parameter Rowseterstellung](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md).|  
|IOpenRowset::OpenRowset|Wird verwendet, wenn Sie den Typ eines Tabellenwertparameters nicht kennen und ein Tabellenwertparameter-Rowsetobjekt anhand der vom Server abgerufenen Metadateninformationen instanziieren möchten.<br /><br /> Weitere Informationen finden Sie unter "Dynamischen Szenario" in [Table-Valued Parameter Rowseterstellung](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md).|  
|ISSCommandWithParameters::SetParameterInfo|Zur Bezeichnung eines Tabellenwert-Befehlsparameters gibt der Consumer im *pwszName*-Element der DBPARAMBINDINFO-Struktur den Typ des Parameters als „table“ oder DBTYPE_TABLE an. Die *UlParamSize* nastaven NA hodnotu ~ 0. Weitere Informationen finden Sie unter "Tabellenwertparameter-Spezifikation" in [Executing Commands Containing Table-Valued Parameter](../../oledb/ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md).|  
|ISSCommandWithParameters::SetParameterProperties|Legt spezielle Eigenschaften für Tabellenwertparameter fest, z. B. Schemaname, Typname, Spaltenreihenfolge und Standardspalten.<br /><br /> Der Consumer gibt die Ordnungszahl des Parameterwerts unter *iOrdinal* in der SSPARAMPROPS-Struktur an. Die angeforderte Eigenschaftengruppe ist DBPROPSET_SQLSERVERPARAMETER.|  
|ISSCommandWithParameters::GetParameterInfo|Ruft die Typen aller Parameter zu einem angegebenen Befehl ab.<br /><br /> Für Tabellenwertparameter verfügt das *wType*-Feld in der DBPARAMINFO-Struktur über den Typ DBTYPE_TABLE. Das *ulParamSize*-Feld wird auf ~0 festgelegt, um anzugeben, dass die Länge unbekannt ist.|  
|ISSCommandWithParameters::GetParameterProperties|Ruft weitere Typinformationen für Parameter des DBTYPE_TABLE-Typs ab.<br /><br /> Der Consumer gibt die Ordnungszahl des Parameterwerts im *iOrdinal*-Element der SSPARAMPROPS-Struktur an. Der Consumer kann beliebige Eigenschaften der DBPROPSET_SQLSERVERPARAMETER-Eigenschaftengruppe anfordern, die unter  aufgeführt sind.<br /><br /> Da der Consumer den Tabellenwertparameter-Typ nicht kennt, muss der Anbieter für SSPROP_PARAM_TYPE_TYPENAME, SSPROP_PARAM_TYPE_SCHEMANAME und SSPROP_PARAM_TYPE_CATALOGNAME die korrekten Werte festlegen. Die übrigen Eigenschaften, SSPROP_PARAM_TABLE_DEFAULT_COLUMNS und SSPROP_PARAM_TABLE_COLUMN_SORT_ORDER, behalten ihre Standardwerte. Nachdem der Consumer den Tabellenwertparameter-Typnamen erkannt hat, erstellt er mithilfe von IOpenRowset::OpenRowset eine Instanz dieses Tabellenwertparameters. Dabei wird der Name des Tabellenwertparameter-Typs angegeben. Weitere Informationen finden Sie unter [Table-Valued Parameter Typermittlung](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md).|  
|IRowsetInfo:: GetProperties|Ruft Tabellenwertparameter-Rowseteigenschaften ab. Der Consumer kann diese Eigenschaften verwenden, um Bindungen optimal einzurichten.|  
|IColumnsRowset::GetColumnsRowset|Ruft Metadateninformationen zu einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle ab. Für Tabellenwertparameter stellt diese Schnittstelle ausführliche Metadateninformationen über jede Spalte bereit, darunter:<br /><br /> DBCOLUMN_FLAGS gibt die NULL-Zulässigkeit durch das DBCOLUMNFLAGS_ISNULLABLE-Bit an.<br /><br /> DBCOLUMN_ISUNIQUE gibt an, ob es sich bei der Spalte um eine Identitätsspalte handelt.<br /><br /> DBCOLUMN_COMPUTEMODE gibt an, ob die Spalte berechnet wird.|  
|IAccessor:: CreateAccessor|Um ein Tabellenwertparameter-Rowsetobjekt an einen Befehlsparameter zu binden, erstellen Sie einen Accessor. Für das *wType*-Element wird dabei DBTYPE_TABLE festgelegt. Die DBOBJECT-Struktur enthält IID_IRowset oder eine beliebige andere gültige Rowsetobjekt-Schnittstelle im *iid*-Element. Die übrigen Felder werden ähnlich behandelt wie DBTYPE_IUNKNOWN.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OLE DB-Typunterstützung für Tabellenwertparameter](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)   
 [Tabellenwertparameter-Rowseterstellung](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)   
 [Verwenden von Tabellenwertparametern &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
