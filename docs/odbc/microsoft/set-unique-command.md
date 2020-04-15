---
title: SET UNIQUE Befehl | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7d3d37509450d1305891100b37bfd1ad026166e8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300840"
---
# <a name="set-unique-command"></a>SET UNIQUE-Befehl
Gibt an, ob Datensätze mit doppelten Indexschlüsselwerten in einer Indexdatei verwaltet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>Argumente  
 EIN  
 Gibt an, dass jeder Datensatz mit einem doppelten Indexschlüsselwert nicht in die Indexdatei aufgenommen wird. Nur der erste Datensatz mit dem ursprünglichen Indexschlüsselwert ist in der Indexdatei enthalten.  
  
 OFF  
 (Standard.) Gibt an, dass Datensätze mit doppelten Indexschlüsselwerten in die Indexdatei aufgenommen werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Eine Indexdatei behält ihre SET UNIQUE-Einstellung bei, wenn Sie REINDEX ausstellen. Weitere Informationen finden Sie unter [INDEX](../../odbc/microsoft/index-command.md).
