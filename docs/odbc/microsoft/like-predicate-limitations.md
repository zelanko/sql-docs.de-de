---
title: LIKE Prädikat Einschränkungen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6d596d688956d7bdbf3d9125184d81c16249781c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298960"
---
# <a name="like-predicate-limitations"></a>Einschränkungen des LIKE-Prädikats
Wenn Daten in einer Spalte länger als 255 Zeichen sind, basiert der LIKE-Vergleich nur auf den ersten 255 Zeichen.  
  
 Ein IN einer Prozedur verwendetes LIKE wird nur mit konstanten Mustern unterstützt. Die Desktopdatenbanktreiber unterstützen den SQL-92 LIKE-Musterabgleich.  
  
 Die Verwendung einer Escapeklausel in einem LIKE-Prädikat wird nicht unterstützt.  
  
 Ein LIKE-Vergleich sollte nicht für eine Spalte durchgeführt werden, die Daten eines numerischen oder Float-Datentyps enthält. Die Ergebnisse können unvorhersehbar sein. Weitere Informationen finden Sie im *Microsoft Jet Database Engine Programmer es Guide*.
