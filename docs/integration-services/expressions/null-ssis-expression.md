---
title: NULL (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- NULL function
- null values [Integration Services]
ms.assetid: df144237-3fbb-41ac-8624-efd92b6522b9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f6e94c381e6303d380b2d1447f98299a0f28ec89
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65725160"
---
# <a name="null-ssis-expression"></a>NULL (SSIS-Ausdruck)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Gibt einen NULL-Wert eines angeforderten Datentyps zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
NULL(typespec)  
```  
  
## <a name="arguments"></a>Argumente  
 *typespec*  
 Ein gültiger Datentyp. Weitere Informationen finden Sie unter [Integration Services Datentypen](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 Ein beliebiger gültiger Datentyp mit einem NULL-Wert.  
  
## <a name="remarks"></a>Remarks  
 NULL gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
 Parameter sind erforderlich, um einen NULL-Wert für bestimmte Datentypen anzufordern. In der folgenden Tabelle sind diese Datentypen und die zugehörigen Parameter aufgelistet.  
  
|Datentyp|Parameter|Beispiel|  
|---------------|---------------|-------------|  
|DT_STR|*charcount*<br /><br /> *codepage*|(DT_STR,30,1252) wandelt 30 Zeichen mithilfe der 1252-Codepage in den DT_STR-Datentyp um.|  
|DT_WSTR|*charcount*|(DT_WSTR,20) wandelt 20 Zeichen in den DT_WSTR-Datentyp um.|  
|DT_BYTES|*bytecount*|(DT_BYTES,50) wandelt 50 Bytes in den DT_BYTES-Datentyp um.|  
|DT_DECIMAL|*scale*|(DT_DECIMAL,2) wandelt einen numerischen Wert mithilfe von 2 Dezimalstellen in den DT_DECIMAL-Datentyp um.|  
|DT_NUMERIC|*precision*<br /><br /> *scale*|(DT_NUMERIC,10,3) wandelt einen numerischen Wert mithilfe einer Genauigkeit von 10 und 3 Dezimalstellen in den DT_NUMERIC-Datentyp um.|  
|DT_TEXT|*codepage*|(DT_TEXT,1252) wandelt einen Wert mithilfe der 1252-Codepage in den DT_TEXT-Datentyp um.|  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesen Beispielen wird der NULL-Wert der Datentypen zurückgegeben: DT_STR, DT_DATE und DT_BOOL.  
  
```  
NULL(DT_STR,10,1252)  
NULL(DT_DATE)  
NULL(DT_BOOL)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ISNULL &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/isnull-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
