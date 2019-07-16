---
title: OPENROWSET (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8be3fe8cbf30121ec2895f59306c925a422d5c39
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67938126"
---
# <a name="ltsource-data-querygt---openrowset"></a>&lt;quelldatenabfrage&gt; -OPENROWSET
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Ersetzt die Quelldatenabfrage durch eine Abfrage an einen externen Anbieter. Die Anweisungen INSERT, SELECT FROM PREDICTION JOIN und SELECT FROM NATURAL PREDICTION JOIN unterstützen **OPENROWSET**.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
OPENROWSET(provider_name,provider_string,query_syntax)  
```  
  
## <a name="arguments"></a>Argumente  
 *provider_name*  
 Der Name eines OLE DB-Anbieters.  
  
 *provider_string*  
 Die OLE DB-Verbindungszeichenfolge für den angegebenen Anbieter.  
  
 *query_syntax*  
 Eine Abfragesyntax, die ein Rowset zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die Datamining-Anbieter Herstellen einer Verbindung mit dem Datenquellenobjekt mit *Provider_name* und *Provider_string,* und führt die Abfrage im angegebenen *Query_syntax* um das Rowset aus den Quelldaten abzurufen.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel kann in einer PREDICTION JOIN-Anweisung verwendet werden, um Daten mit einer [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]-SELECT-Anweisung aus der [!INCLUDE[tsql](../includes/tsql-md.md)]-Datenbank abzurufen.  
  
```  
OPENROWSET  
(  
'SQLOLEDB.1',  
'Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security     Info=False;Initial Catalog=AdventureWorksDW2012;Data Source=localhost',  
'SELECT TOP 1000 * FROM vTargetMail'  
)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [&#60;quelldatenabfrage&#62;](../dmx/source-data-query.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
