---
title: ISSCommandWithParameters::GetParameterProperties (OLE DB) | Microsoft-Dokumentation
description: ISSCommandWithParameters::GetParameterProperties gibt ein Array von Eigenschaftssatzstrukturen im OLE DB-Treiber für SQL Server zurück, eine für jeden UDT- oder XML-Parameter.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- GetParameterProperties method
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8631c9c1beed054b57fd368dd567e3568c213b50
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862147"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>'ISSCommandWithParameters::GetParameterProperties' (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Gibt ein Array aus SSPARAMPROPS-Eigenschaftensatzstrukturen zurück – einen SSPARAMPROPS-Eigenschaftensatz für jeden UDT- oder XML-Parameter.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT GetParameterProperties(  
      DB_UPARAMS *pcParams,  
      SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a>Argumente  
 *pcParams*[out] [in]  
 Ein Zeiger auf den Arbeitsspeicher, der die Anzahl von SSPARAMPROPS-Strukturen enthält, die in *prgParamProperties*zurückgegeben werden.  
  
 *prgParamProperties*[out]  
 Ein Zeiger auf den Arbeitsspeicher, in den ein Array aus SSPARAMPROPS-Strukturen zurückgegeben wird. Der Anbieter teilt Arbeitsspeicher für die Strukturen zu und gibt die Adresse an diesen Arbeitsspeicher zurück. Der Consumer gibt diesen Arbeitsspeicher mit `IMalloc::Free` frei, wenn er die Strukturen nicht mehr benötigt. Bevor der Consumer `IMalloc::Free` für *prgParamProperties* aufrufen kann, muss er auch für die *vValue*-Eigenschaft jeder DBPROP-Struktur `VariantClear` aufrufen, um einem Arbeitsspeicherverlust vorzubeugen. Zu diesem kann es kommen, wenn die Variante einen Verweistyp wie z. B. BSTR enthält. Wenn *pcParams* bei der Ausgabe 0 (null) ist oder ein anderer Fehler als DB_E_ERRORSOCCURRED auftritt, teilt der Anbieter keinen Arbeitsspeicher zu und stellt sicher, dass *prgParamProperties* bei Ausgabe ein NULL-Zeiger ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Die `GetParameterProperties`-Methode gibt die gleichen Fehlercodes wie die OLE DB-Kernmethode `ICommandProperties::GetProperties` zurück, mit der Ausnahme, dass DB_S_ERRORSOCCURRED und DB_E_ERRORSOCCURED nicht ausgelöst werden können.  
  
## <a name="remarks"></a>Bemerkungen  
 Die `ISSCommandWithParameters::GetParameterProperties`-Methode verhält sich in Bezug auf `GetParameterInfo` konsistent. Wenn [`ISSCommandWithParameters::SetParameterProperties`](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) oder `SetParameterInfo` nicht aufgerufen wurden oder mit cParams gleich 0 aufgerufen wurden, leitet `GetParameterInfo` Parameterinformationen ab und gibt sie zurück. Wenn `ISSCommandWithParameters::SetParameterProperties` oder `SetParameterInfo` für mindestens einen Parameter aufgerufen wurden, gibt die `ISSCommandWithParameters::GetParameterProperties`-Methode Eigenschaften nur für diejenigen Parameter zurück, für die `ISSCommandWithParameters::SetParameterProperties` aufgerufen wurde. Wenn `ISSCommandWithParameters::SetParameterProperties` nach `ISSCommandWithParameters::GetParameterProperties` oder `GetParameterInfo` aufgerufen wird, geben nachfolgende Aufrufe von `ISSCommandWithParameters::GetParameterProperties` die überschriebenen Werte für diejenigen Parameter zurück, für die die `ISSCommandWithParameters::SetParameterProperties`-Methode aufgerufen wurde.  
  
 Die SSPARAMPROPS-Struktur ist folgendermaßen definiert:  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|Member|BESCHREIBUNG|  
|------------|-----------------|  
|*iOrdinal*|Die Ordnungszahl des übergebenen Parameters|  
|*cPropertySets*|Die Anzahl von DBPROPSET-Strukturen in *rgPropertySets*|  
|*rgPropertySets*|Ein Zeiger auf den Speicher, in den ein Array aus DBPROPSET-Strukturen zurückgegeben werden soll|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
