---
title: LIKE-Prädikat Einschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8cd3cebfcf20df2f8a3a786ea66fd28dd76307c0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68119709"
---
# <a name="like-predicate-limitations"></a>Einschränkungen des LIKE-Prädikats
Wenn die Daten in einer Spalte mehr als 255 Zeichen enthalten, basiert der Like-Vergleich nur auf den ersten 255 Zeichen.  
  
 Ein like, der in einer Prozedur verwendet wird, wird nur mit Konstanten Mustern unterstützt. Die Desktop-Datenbanktreiber unterstützen SQL-92 wie Musterabgleich.  
  
 Die Verwendung einer Escape-Klausel in einem LIKE-Prädikat wird nicht unterstützt.  
  
 Ein Like-Vergleich sollte nicht für eine Spalte mit Daten eines numerischen Datentyps oder eines float-Datentyps ausgeführt werden. Die Ergebnisse sind möglicherweise nicht vorhersehbar. Weitere Informationen finden Sie im *Microsoft Jet Datenbank-Engine Programmer es Guide*.
