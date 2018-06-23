---
title: GETDATE (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9161d114b9f103dc857c26a07b3c107d14a00b40
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160248"
---
# <a name="getdate-ssis-expression"></a>GETDATE (SSIS-Ausdruck)
  Gibt das aktuelle Datum des Systems in einem DT_DBTIMESTAMP-Format zurück. Die GETDATE-Funktion weist keine Argumente auf.  
  
> [!NOTE]  
>  Die Länge des von der GETDATE-Funktion zurückgegebenen Ergebnisses beträgt 29 Zeichen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
GETDATE()  
```  
  
## <a name="arguments"></a>Argumente  
 InclusionThresholdSetting  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [GETUTCDATE &#40;SSIS-Ausdruck&#41;](getutcdate-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  