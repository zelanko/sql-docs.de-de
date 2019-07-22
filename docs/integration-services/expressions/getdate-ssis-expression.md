---
title: GETDATE (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 492e3f702fc5ae851a6d78aae2df5fa26e5ca379
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68080934"
---
# <a name="getdate-ssis-expression"></a>GETDATE (SSIS-Ausdruck)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Gibt das aktuelle Datum des Systems in einem DT_DBTIMESTAMP-Format zurück. Die GETDATE-Funktion weist keine Argumente auf.  
  
> [!NOTE]  
>  Die Länge des von der GETDATE-Funktion zurückgegebenen Ergebnisses beträgt 29 Zeichen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
GETDATE()  
```  
  
## <a name="arguments"></a>Argumente  
 None  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird das Jahr des aktuellen Datums zurückgegeben.  
  
```  
DATEPART("year",GETDATE())  
```  
  
 In diesem Beispiel wird die Anzahl von Tagen zwischen einem Datum in der **ModifiedDate** -Spalte und dem aktuellen Datum zurückgegeben.  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 In diesem Beispiel werden dem aktuellen Datum drei Monate hinzugefügt.  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [GETUTCDATE &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/getutcdate-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
