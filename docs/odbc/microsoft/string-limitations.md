---
title: String-Einschränkungen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7faab41bd52397ac0d352e04a9ec153571e93f1e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67948762"
---
# <a name="string-limitations"></a>Einschränkungen für Zeichenfolgen
Die maximale Länge einer Zeichenfolge der SQL-Anweisung ist 65.000 Zeichen.  
  
 Wenn die Microsoft Access-Treiber verwendet wird, werden nur SQL-92 Zeichenfolgenkonstanten (in einfache Anführungszeichen, keine doppelten Anführungszeichen) unterstützt.  
  
 Das Pipezeichen (&#124;) kann nicht in einer Zeichenfolge verwendet werden, ob das Zeichen in Back Anführungszeichen oder nicht eingeschlossen ist.  
  
 Für eine optimale Interoperabilität sollten Anwendungen Zeichenfolgen übergeben, in-Parameter, anstatt übergeben in Anführungszeichen in Zeichenfolgen.
