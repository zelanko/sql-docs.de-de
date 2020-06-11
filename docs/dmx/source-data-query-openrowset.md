---
title: OPENROWSET (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 125fe829c3b76be0d92a3519249df571890efbf2
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83670019"
---
# <a name="ltsource-data-querygt---openrowset"></a>&lt;Quelldaten Abfrage &gt; -OPENROWSET
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Ersetzt die Quelldatenabfrage durch eine Abfrage an einen externen Anbieter. Die Anweisungen INSERT, Select from Vorhersage Join und SELECT from Natural Vorhersage Join unterstützen **OPENROWSET**.  
  
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
  
## <a name="remarks"></a>Bemerkungen  
 Der Data Mining-Anbieter stellt mithilfe *provider_name* und provider_string eine Verbindung mit dem Datenquellen Objekt her und führt die in *query_syntax* angegebene Abfrage aus *,* um das Rowset aus den Quelldaten abzurufen.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [&#60;Quelldaten Abfrage&#62;](../dmx/source-data-query.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
