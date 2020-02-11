---
title: 'ISSCommandWithParameters:: SetParameterProperties (OLE DB) | Microsoft-Dokumentation'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 778021ce007f0c1eac68197e0c07e2cb7b0bb001
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62638771"
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
 *cparameams*[in]  
 Die Anzahl der SSPARAMPROPS-Strukturen im *rgParamProperties*-Array. Wenn diese Zahl 0 (NULL `ISSCommandWithParameters::SetParameterProperties` ) ist, werden alle Eigenschaften gelöscht, die möglicherweise für Parameter im Befehl angegeben wurden.  
  
 *rgParamProperties*[in]  
 Ein Array von SSPARAMPROPS-Strukturen, die festgelegt werden sollen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Die `ISSCommandWithParameters::SetParameterProperties` -Methode gibt dieselben Fehlercodes zurück wie die Core-OLE DB **ICommandProperties:: SetProperties** -Methode.  
  
## <a name="remarks"></a>Bemerkungen  
 Das Festlegen von Parameter Eigenschaften mit dieser Methode ist für eine Parameter Basis nach Ordinalzahl oder mit einem einzelnen `ISSCommandWithParameters::SetParameterProperties` -Befehl zulässig, sobald ssparamproperties aus dem Eigenschafts Array erstellt wurde.  
  
 Die **SetParameterInfo** -Methode muss aufgerufen werden, bevor `ISSCommandWithParameters::SetParameterProperties` die-Methode aufgerufen wird. Durch Aufrufen von `SetParameterProperties(0, NULL)` werden alle angegebenen Parametereigenschaften gelöscht, während der Aufruf von `SetParameterInfo(0,NULL,NULL)` alle Parameterinformationen löscht, einschließlich Eigenschaften, die einem Parameter zugeordnet sind.  
  
 Der `ISSCommandWithParameters::SetParameterProperties` Aufruf von zum Angeben von Eigenschaften für einen Parameter, der nicht vom Typ DBTYPE_XML oder DBTYPE_UDT DB_E_ERRORSOCCURRED oder DB_S_ERRORSOCCURRED zurückgibt, und kennzeichnet das *dwStatus* -Feld aller dbproperties, die in ssparamproperties für diesen Parameter mit DBPROPSTATUS_NOTSET enthalten sind. Das DBPROP-Array jedes in SSPARAMPROPS enthaltenen DBPROPs sollte durchsucht werden, um zu ermitteln, auf welchen Parameter DB_E_ERRORSOCCURRED bzw. DB_S_ERRORSOCCURRED verweist.  
  
 Wenn `ISSCommandWithParameters::SetParameterProperties` aufgerufen wird, um die Eigenschaften von Parametern anzugeben, deren Parameterinformationen noch nicht mit **SetParameterInfo**festgelegt wurden, gibt der Anbieter E_UNEXPECTED mit der folgenden Fehlermeldung zurück:  
  
 Die SetParameterProperties-Methode kann für die angegebenen Parameter nicht aufgerufen werden, ohne dass zunächst die SetParameterInfo-Methode aufgerufen wird. Die Parameterinformationen müssen vor dem Festlegen der Parametereigenschaften festgelegt werden.  
  
 Wenn der Aufrufen von `ISSCommandWithParameters::SetParameterProperties` einige Parameter enthält, bei denen die Parameterinformationen festgelegt wurden, und einige Parameter, bei denen die Parameterinformationen nicht festgelegt wurden, werden die dwStatus-Eigenschaften im DBPROPSET der ssparamproperties-Eigenschaft mit DBSTATUS_NOTSET zurückgegeben.  
  
 Die SSPARAMPROPS-Struktur ist folgendermaßen definiert:  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 Verbesserungen in der Datenbank- [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Engine, beginnend mit "ISSCommandWithParameters:: SetParameterProperties", um genauere Beschreibungen der erwarteten Ergebnisse zu erhalten. Diese präziseren Ergebnisse können sich von den Werten unterscheiden, die von ISSCommandWithParameters:: SetParameterProperties in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]früheren Versionen von zurückgegeben wurden. Weitere Informationen finden Sie unter [metadatenermittlung](../native-client/features/metadata-discovery.md).  
  
|Mitglied|BESCHREIBUNG|  
|------------|-----------------|  
|*iOrdinal*|Die Ordnungszahl des übergebenen Parameters|  
|*cpropertysets*|Die Anzahl von DBPROPSET-Strukturen in *rgPropertySets*|  
|*rgPropertySets*|Ein Zeiger auf den Speicher, in den ein Array aus DBPROPSET-Strukturen zurückgegeben werden soll|  
  
## <a name="see-also"></a>Weitere Informationen  
 [' ISSCommandWithParameters ' &#40;OLE DB&#41;](isscommandwithparameters-ole-db.md)  
  
  
