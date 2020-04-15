---
title: String-Einschränkungen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61f81ff3da882095a0a6c41bb5061addd497a5d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306061"
---
# <a name="string-limitations"></a>Einschränkungen für Zeichenfolgen
Die maximale Länge einer SQL-Anweisungszeichenfolge beträgt 65.000 Zeichen.  
  
 Wenn der Microsoft Access-Treiber verwendet wird, werden nur SQL-92-Zeichenfolgenkonstanten (mit einzelnen Anführungszeichen, nicht mit doppelten Anführungszeichen) unterstützt.  
  
 Das Pipe-Zeichen (&#124;) kann nicht in einer Zeichenfolge verwendet werden, unabhängig davon, ob das Zeichen in hintere Anführungszeichen eingeschlossen ist oder nicht.  
  
 Für maximale Interoperabilität sollten Anwendungen Zeichenfolgen in Parametern übergeben, anstatt zitierte Zeichenfolgen zu übergeben.
