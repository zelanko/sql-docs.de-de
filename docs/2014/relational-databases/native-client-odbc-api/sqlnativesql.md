---
title: SQLNativeSql | Microsoft Docs
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
topic_type:
- apiref
helpviewer_keywords:
- SQLNativeSql function
ms.assetid: 2d999fec-9e22-4514-ad5f-22a64b82f95b
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c24e849b1082e3b5e4ac2f95f8c880cd70e2cc75
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162461"
---
# <a name="sqlnativesql"></a>SQLNativeSql
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber erfüllt **SQLNativeSql** -Anforderungen, ohne auf den Server zuzugreifen. Die Funktion testet die Syntax von SQL-Anweisungen effizient. Durch die Syntaxüberprüfung wird nicht bestimmt, ob Bezeichner oder die Ergebnisse von Ausdrücken in den SQL-Anweisungen gültig sind, und systemeigene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL-Anweisungen, die von **SQLNativeSql** zurückgegeben werden, können möglicherweise nicht ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLNativeSql-Funktion](http://go.microsoft.com/fwlink/?LinkID=59358)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  