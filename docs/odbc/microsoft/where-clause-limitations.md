---
title: Einschränkungen der WHERE-Klausel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, WHERE clause limitations
- WHERE clause limitations [ODBC]
ms.assetid: 46b54f74-e4a3-4318-87cf-8a97c38a2718
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3bb6194d93e545526a850443f5e97074d88e7e1b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67911424"
---
# <a name="where-clause-limitations"></a>Einschränkungen der WHERE-Klausel
Die maximale Anzahl von Klauseln in einer WHERE-Klausel ist 40.  
  
 Die Spalten LONGVARBINARY und LONGVARCHAR können mit literalen von bis zu 255 Zeichen verglichen werden, können aber nicht mit Parametern verglichen werden.
