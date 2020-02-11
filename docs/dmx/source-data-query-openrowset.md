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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938126"
---
# <a name="ltsource-data-querygt---openrowset"></a>&lt;Quelldaten Abfrage&gt; -OPENROWSET
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
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
