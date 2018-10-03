---
title: 'Isscommandwithparameters:: Getparameterproperties (OLE DB) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f8e13ede890599c7424c2bb181a966608b09b0b5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47686644"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>'ISSCommandWithParameters::GetParameterProperties' (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

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
 Ein Zeiger auf den Arbeitsspeicher, in den ein Array aus SSPARAMPROPS-Strukturen zurückgegeben wird. Der Anbieter teilt Speicher für die Strukturen zu und gibt die Adresse an den Arbeitsspeicher zurück. Der Consumer gibt diesen Speicher mit **IMalloc::Free** frei, wenn er die Strukturen nicht mehr benötigt. Vor dem Aufruf **IMalloc:: Free** für *PrgParamProperties*, der Consumer muss auch aufrufen, **VariantClear** für die *vValue* Eigenschaft Geben Sie jeder DBPROP-Struktur, um einen Speicherverlust zu vermeiden, in denen die Variante einen Verweis enthält (z. B. BSTR). Wenn *PcParams* ist 0 (null) bei der Ausgabe oder ein anderer Fehler als DB_E_ERRORSOCCURRED auftritt, der Anbieter keinen Speicher belegen wird und stellt sicher, dass *PrgParamProperties* bei der Ausgabe ein null-Zeiger ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Die **GetParameterProperties** -Methode gibt dieselben Fehlercodes zurück wie die OLE DB **ICommandProperties::GetProperties** -Methode, allerdings können DB_S_ERRORSOCCURRED und DB_E_ERRORSOCCURED nicht ausgelöst werden.  
  
## <a name="remarks"></a>Hinweise  
 **ISSCommandWithParameters::GetParameterProperties** verhält sich in Bezug auf **GetParameterInfo**konsistent. Wenn [isscommandwithparameters:: SetParameterProperties](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) oder **SetParameterInfo** nicht aufgerufen wurde oder gleich 0 (null), einem aufgerufen worden **GetParameterInfo**Parameterinformationen abgeleitet, und gibt diese zurück. Wenn **ISSCommandWithParameters::SetParameterProperties** oder **SetParameterInfo** für mindestens einen Parameter aufgerufen wurde, gibt **ISSCommandWithParameters::GetParameterProperties** Eigenschaften nur für die Parameter zurück, für die **ISSCommandWithParameters::SetParameterProperties** aufgerufen wurde. Wenn **ISSCommandWithParameters::SetParameterProperties** nach **ISSCommandWithParameters::GetParameterProperties** oder **GetParameterInfo**aufgerufen wird, geben nachfolgende Aufrufe von **ISSCommandWithParameters::GetParameterProperties** die überschriebenen Werte für jene Parameter zurück, für die **ISSCommandWithParameters::SetParameterProperties** aufgerufen wurde.  
  
 Die SSPARAMPROPS-Struktur ist folgendermaßen definiert:  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|Member|Description|  
|------------|-----------------|  
|*iOrdinal*|Die Ordnungszahl des übergebenen Parameters|  
|*cPropertySets*|Die Anzahl von DBPROPSET-Strukturen in *rgPropertySets*|  
|*rgPropertySets*|Ein Zeiger auf den Speicher, in den ein Array aus DBPROPSET-Strukturen zurückgegeben werden soll|  
  
## <a name="see-also"></a>Siehe auch  
 [ISSCommandWithParameters &#40;OLE-DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
