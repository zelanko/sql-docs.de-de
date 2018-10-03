---
title: Befehl SET UNIQUE | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET UNIQUE command [ODBC]
ms.assetid: 1f69e31e-4599-47cc-ac89-b86fba8703c5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f58eb771245b9820e27ca4d14c2f69035effa44
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692118"
---
# <a name="set-unique-command"></a>SET UNIQUE-Befehl
Gibt an, ob Datensätze mit doppelten Indexschlüsselwerten in eine Indexdatei beibehalten werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>Argumente  
 ON  
 Gibt an, dass alle Datensätze mit einem doppelten Indexschlüsselwerten-Schlüsselwert in der Indexdatei nicht enthalten sein. Nur der erste Datensatz mit dem ursprünglichen Wert des Index befindet sich in der Indexdatei.  
  
 OFF  
 (Standard). Gibt an, dass die Indexdatei Datensätze mit doppelten Indexschlüsselwerten berücksichtigt werden.  
  
## <a name="remarks"></a>Hinweise  
 Eine Indexdatei behält seine eindeutige festgelegt Einstellung an, beim REINDEX ausgeben. Weitere Informationen finden Sie unter [INDEX](../../odbc/microsoft/index-command.md).
