---
title: 'Isscommandwithparameters:: SetParameterProperties (OLE DB) | Microsoft Docs'
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
api_name:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f17947c2b5eb0a8438c074ffca34dca728ae859a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057838"
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
 Die Anzahl der SSPARAMPROPS-Strukturen in den *RgParamProperties* Array. Wenn diese Anzahl Null ist, `ISSCommandWithParameters::SetParameterProperties` werden alle Eigenschaften, die für alle Parameter im Befehl angegeben wurden möglicherweise gelöscht.  
  
 *RgParamProperties*[in]  
 Ein Array von SSPARAMPROPS-Strukturen, die festgelegt werden sollen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Die `ISSCommandWithParameters::SetParameterProperties` Methodenrückgabe die gleichen Fehlercodes wie die OLE DB- **ICommandProperties:: SetProperties** Methode.  
  
## <a name="remarks"></a>Hinweise  
 Festlegen von Parametereigenschaften mit dieser Methode ist zulässig auf einer einzelparameterbasis nach Ordnungszahl oder mit einem einzelnen `ISSCommandWithParameters::SetParameterProperties` aufrufen, sobald der SSPARAMPROPS aus dem Eigenschaftsarray erstellt wurde.  
  
 Die **SetParameterInfo** Methode muss aufgerufen werden, bevor die `ISSCommandWithParameters::SetParameterProperties` Methode. Durch Aufrufen von `SetParameterProperties(0, NULL)` werden alle angegebenen Parametereigenschaften gelöscht, während der Aufruf von `SetParameterInfo(0,NULL,NULL)` alle Parameterinformationen löscht, einschließlich Eigenschaften, die einem Parameter zugeordnet sind.  
  
 Aufrufen von `ISSCommandWithParameters::SetParameterProperties` Eigenschaften für einen Parameter angeben, die nicht vom Typ gibt DBTYPE_XML- oder DBTYPE_UDT DB_E_ERRORSOCCURRED oder DB_S_ERRORSOCCURRED und kennzeichnet die *DwStatus* aller in SSPARAMPROPS enthaltenen DBPROPs Feld für diesen Parameter mit DBPROPSTATUS_NOTSET. Das DBPROP-Array jedes in SSPARAMPROPS enthaltenen DBPROPs sollte durchsucht werden, um zu ermitteln, auf welchen Parameter DB_E_ERRORSOCCURRED bzw. DB_S_ERRORSOCCURRED verweist.  
  
 Wenn `ISSCommandWithParameters::SetParameterProperties` wird aufgerufen, um Geben Sie die Eigenschaften von Parametern, deren Parameterinformationen wurde mit nicht noch festgelegt **SetParameterInfo**, gibt der Anbieter E_UNEXPECTED zurück, mit der folgenden Fehlermeldung:  
  
 Die SetParameterProperties-Methode kann für die angegebenen Parameter nicht aufgerufen werden, ohne dass zunächst die SetParameterInfo-Methode aufgerufen wird. Die Parameterinformationen müssen vor dem Festlegen der Parametereigenschaften festgelegt werden.  
  
 Wenn der Aufruf von `ISSCommandWithParameters::SetParameterProperties` enthält einige Parameter, in denen Parameterinformationen festgelegt wurde, und einige Parameter, in denen Parameterinformationen nicht festgelegt wurde, wird die DwStatus-Eigenschaften im DBPROPSET der SSPARAMPROPS-Eigenschaftensatz mit DBSTATUS_NOTSET zurückgegeben.  
  
 Die SSPARAMPROPS-Struktur ist folgendermaßen definiert:  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 Verbesserungen im Datenbankmodul ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] isscommandwithparameters:: SetParameterProperties genauere Beschreibungen der erwarteten Ergebnisse abrufen können. Diese genaueren Ergebnisse unterscheidet sich möglicherweise von der Rückgabewerte isscommandwithparameters:: SetParameterProperties in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Metadatenermittlung](../native-client/features/metadata-discovery.md).  
  
|Member|Description|  
|------------|-----------------|  
|*iOrdinal*|Die Ordnungszahl des übergebenen Parameters|  
|*cPropertySets*|Die Anzahl von DBPROPSET-Strukturen in *rgPropertySets*|  
|*rgPropertySets*|Ein Zeiger auf den Speicher, in den ein Array aus DBPROPSET-Strukturen zurückgegeben werden soll|  
  
## <a name="see-also"></a>Siehe auch  
 [ISSCommandWithParameters &#40;OLE DB&#41;](isscommandwithparameters-ole-db.md)  
  
  