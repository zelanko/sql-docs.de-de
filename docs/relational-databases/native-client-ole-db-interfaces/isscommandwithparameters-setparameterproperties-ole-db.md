---
title: "'ISSCommandWithParameters::SetParameterProperties' (OLE DB)"
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 80cf43e4abc1be19b1a6033174c980aa6d7cd378
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81290185"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a>'ISSCommandWithParameters::SetParameterProperties' (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Legt die Parametereigenschaften für einzelne Parameter nach Ordnungszahl fest oder legt Massenparametereigenschaften durch Angabe eines Arrays von SSPARAMPROPS-Strukturen fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetParameterProperties(  
      DB_UPARAMS cParams,   
      SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a>Argumente  
 *cParams*[in]  
 Die Anzahl der SSPARAMPROPS-Strukturen im *rgParamProperties*-Array. Wenn diese Anzahl 0 ist, löscht **ISSCommandWithParameters::SetParameterProperties** alle Eigenschaften, die für Parameter im Befehl möglicherweise festgelegt wurden.  
  
 *rgParamProperties*[in]  
 Ein Array von SSPARAMPROPS-Strukturen, die festgelegt werden sollen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Die **ISSCommandWithParameters::SetParameterProperties**-Methode gibt die gleichen Fehlercodes wie die OLE DB-Kernmethode **ICommandProperties::SetProperties** zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Das Festlegen von Parametereigenschaften mit dieser Methode ist auf Einzelparameterbasis nach Ordnungszahl oder mit einem einzelnen **ISSCommandWithParameters::SetParameterProperties**-Aufruf zulässig, sobald SSPARAMPROPS aus dem Eigenschaftenarray aufgebaut wurde.  
  
 Die **SetParameterInfo**-Methode muss aufgerufen werden, bevor die **ISSCommandWithParameters::SetParameterProperties**-Methode aufgerufen wird. Durch Aufrufen von `SetParameterProperties(0, NULL)` werden alle angegebenen Parametereigenschaften gelöscht, während der Aufruf von `SetParameterInfo(0,NULL,NULL)` alle Parameterinformationen löscht, einschließlich Eigenschaften, die einem Parameter zugeordnet sind.  
  
 Der Aufruf von **ISSCommandWithParameters:: SetParameterProperties** zum Angeben von Eigenschaften für einen Parameter, der nicht vom Typ DBTYPE_XML oder DBTYPE_UDT gibt DB_E_ERRORSOCCURRED oder DB_S_ERRORSOCCURRED zurück und markiert das Feld *dwStatus* aller in ssparamproperties enthaltenen dbproperties-Werte für diesen Parameter mit DBPROPSTATUS_NOTSET. Das DBPROP-Array jedes in SSPARAMPROPS enthaltenen DBPROPs sollte durchsucht werden, um zu ermitteln, auf welchen Parameter DB_E_ERRORSOCCURRED bzw. DB_S_ERRORSOCCURRED verweist.  
  
 Wenn **ISSCommandWithParameters::SetParameterProperties** aufgerufen wird, um die Eigenschaften von Parametern anzugeben, deren Parameterinformationen noch nicht mit **SetParameterInfo** festgelegt wurden, gibt der Anbieter E_UNEXPECTED mit der folgenden Fehlermeldung zurück:  
  
 Die SetParameterProperties-Methode kann für die angegebenen Parameter nicht aufgerufen werden, ohne dass zunächst die SetParameterInfo-Methode aufgerufen wird. Die Parameterinformationen müssen vor dem Festlegen der Parametereigenschaften festgelegt werden.  
  
 Wenn der Aufruf für **ISSCommandWithParameters::SetParameterProperties** einige Parameter enthält, für die die Parameterinformationen festgelegt wurden, und einige Parameter ohne Parameterinformationen, werden die dwStatus-Eigenschaften im DBPROPSET des SSPARAMPROPS-Eigenschaftensatzes mit DBSTATUS_NOTSET zurückgegeben.  
  
 Die SSPARAMPROPS-Struktur ist folgendermaßen definiert:  

```cpp
struct SSPARAMPROPS {
    DBORDINAL iOrdinal;
    ULONG cPropertySets;
    DBPROPSET *rgPropertySets;
};
```

 Verbesserungen an der Datenbank-Engine ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ermöglichen das Abrufen genauerer Beschreibungen der erwarteten Ergebnisse durch ISSCommandWithParameters::SetParameterProperties. Diese genaueren Ergebnisse unterscheiden sich möglicherweise von den Werten, die in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von SSCommandWithParameters::SetParameterProperties zurückgegeben wurden. Weitere Informationen finden Sie unter [Metadatenermittlung](../../relational-databases/native-client/features/metadata-discovery.md).  
  
|Member|BESCHREIBUNG|  
|------------|-----------------|  
|*iOrdinal*|Die Ordnungszahl des übergebenen Parameters|  
|*cPropertySets*|Die Anzahl von DBPROPSET-Strukturen in *rgPropertySets*|  
|*rgPropertySets*|Ein Zeiger auf den Speicher, in den ein Array aus DBPROPSET-Strukturen zurückgegeben werden soll|  
|||

## <a name="see-also"></a>Weitere Informationen  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
