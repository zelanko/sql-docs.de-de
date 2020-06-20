---
title: ISSCommandWithParameters::SetParameterProperties (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
author: rothja
ms.author: jroth
ms.openlocfilehash: d141c1951066af14e25cb4dd36459f5e87051001
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85056081"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a>'ISSCommandWithParameters::SetParameterProperties' (OLE DB)
  Legt die Parametereigenschaften für einzelne Parameter nach Ordnungszahl fest oder legt Massenparametereigenschaften durch Angabe eines Arrays von SSPARAMPROPS-Strukturen fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT SetParameterProperties(  
DB_UPARAMS cParams,   
SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a>Argumente  
 *cParams*[in]  
 Die Anzahl der SSPARAMPROPS-Strukturen im *rgParamProperties*-Array. Wenn diese Zahl 0 (null) ist, `ISSCommandWithParameters::SetParameterProperties` werden alle Eigenschaften gelöscht, die möglicherweise für Parameter im Befehl angegeben wurden.  
  
 *rgParamProperties*[in]  
 Ein Array von SSPARAMPROPS-Strukturen, die festgelegt werden sollen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Die- `ISSCommandWithParameters::SetParameterProperties` Methode gibt dieselben Fehlercodes zurück wie die Core-OLE DB **ICommandProperties:: SetProperties** -Methode.  
  
## <a name="remarks"></a>Hinweise  
 Das Festlegen von Parameter Eigenschaften mit dieser Methode ist für eine Parameter Basis nach Ordinalzahl oder mit einem einzelnen-Befehl zulässig, `ISSCommandWithParameters::SetParameterProperties` sobald ssparamproperties aus dem Eigenschafts Array erstellt wurde.  
  
 Die **SetParameterInfo** -Methode muss aufgerufen werden, bevor die-Methode aufgerufen wird `ISSCommandWithParameters::SetParameterProperties` . Durch Aufrufen von `SetParameterProperties(0, NULL)` werden alle angegebenen Parametereigenschaften gelöscht, während der Aufruf von `SetParameterInfo(0,NULL,NULL)` alle Parameterinformationen löscht, einschließlich Eigenschaften, die einem Parameter zugeordnet sind.  
  
 `ISSCommandWithParameters::SetParameterProperties`Der Aufruf von zum Angeben von Eigenschaften für einen Parameter, der nicht vom Typ DBTYPE_XML oder DBTYPE_UDT DB_E_ERRORSOCCURRED oder DB_S_ERRORSOCCURRED zurückgibt, und kennzeichnet das *dwStatus* -Feld aller dbproperties, die in ssparamproperties für diesen Parameter mit DBPROPSTATUS_NOTSET enthalten sind. Das DBPROP-Array jedes in SSPARAMPROPS enthaltenen DBPROPs sollte durchsucht werden, um zu ermitteln, auf welchen Parameter DB_E_ERRORSOCCURRED bzw. DB_S_ERRORSOCCURRED verweist.  
  
 Wenn `ISSCommandWithParameters::SetParameterProperties` aufgerufen wird, um die Eigenschaften von Parametern anzugeben, deren Parameterinformationen noch nicht mit **SetParameterInfo**festgelegt wurden, gibt der Anbieter E_UNEXPECTED mit der folgenden Fehlermeldung zurück:  
  
 Die SetParameterProperties-Methode kann für die angegebenen Parameter nicht aufgerufen werden, ohne dass zunächst die SetParameterInfo-Methode aufgerufen wird. Die Parameterinformationen müssen vor dem Festlegen der Parametereigenschaften festgelegt werden.  
  
 Wenn der Aufrufen von `ISSCommandWithParameters::SetParameterProperties` einige Parameter enthält, bei denen die Parameterinformationen festgelegt wurden, und einige Parameter, bei denen die Parameterinformationen nicht festgelegt wurden, werden die dwStatus-Eigenschaften im DBPROPSET der ssparamproperties-Eigenschaft mit DBSTATUS_NOTSET zurückgegeben.  
  
 Die SSPARAMPROPS-Struktur ist folgendermaßen definiert:  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 Verbesserungen an der Datenbank-Engine ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ermöglichen das Abrufen genauerer Beschreibungen der erwarteten Ergebnisse durch ISSCommandWithParameters::SetParameterProperties. Diese genaueren Ergebnisse unterscheiden sich möglicherweise von den Werten, die in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von SSCommandWithParameters::SetParameterProperties zurückgegeben wurden. Weitere Informationen finden Sie unter [Metadatenermittlung](../native-client/features/metadata-discovery.md).  
  
|Member|Beschreibung|  
|------------|-----------------|  
|*iOrdinal*|Die Ordnungszahl des übergebenen Parameters|  
|*cPropertySets*|Die Anzahl von DBPROPSET-Strukturen in *rgPropertySets*|  
|*rgPropertySets*|Ein Zeiger auf den Speicher, in den ein Array aus DBPROPSET-Strukturen zurückgegeben werden soll|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ISSCommandWithParameters &#40;OLE DB&#41;](isscommandwithparameters-ole-db.md)  
  
  
