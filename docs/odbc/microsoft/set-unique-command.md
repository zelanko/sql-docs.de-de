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
ms.openlocfilehash: 29598ed97cba8be04a0c08727cffc40e663becba
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063612"
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
