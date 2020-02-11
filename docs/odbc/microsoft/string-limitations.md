---
title: Einschränkungen für Zeichen folgen | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948762"
---
# <a name="string-limitations"></a>Einschränkungen für Zeichenfolgen
Die maximale Länge einer SQL-Anweisungs Zeichenfolge beträgt 65.000 Zeichen.  
  
 Wenn der Microsoft Access-Treiber verwendet wird, werden nur SQL-92-Zeichen folgen Konstanten (in einfachen Anführungszeichen und nicht in doppelte Anführungszeichen) unterstützt.  
  
 Der senkrechter Strich (&#124;) kann nicht in einer Zeichenfolge verwendet werden, unabhängig davon, ob das Zeichen in backanführungs Zeichen eingeschlossen ist.  
  
 Für eine maximale Interoperabilität sollten Anwendungen Zeichen folgen in Parametern übergeben, anstatt Zeichen folgen in Anführungszeichen zu übergeben.
