---
title: Ausführen von Katalogfunktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], executing
- functions [ODBC], catalog functions
ms.assetid: c59cbda3-e214-4399-9edc-cfac86b378d7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: daf1ab2fc05b198e71b45cb02b4577eebee5c5b6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704288"
---
# <a name="executing-catalog-functions"></a>Ausführen von Katalogfunktionen
Da eine Katalogfunktion auf ein Resultset erstellt wird, ist es gleichbedeutend mit dem Ergebnis Set – Generieren von SQL-Anweisungen ausführen. Katalogfunktionen werden in der Tat häufig implementiert, indem Sie vordefinierte SQL-Anweisungen ausführen oder vordefinierte Schritte ausführen, die mit dem Treiber oder DBMS geliefert werden. Fast alles, das gilt für SQL-Anweisungen, die Resultsets erstellen gilt auch für Katalogfunktionen. Das Anweisungsattribut SQL_ATTR_MAX_ROWS beschränkt z. B. die Anzahl der Zeilen, die von der Katalogfunktion zurückgegeben, genau, wie sie die Anzahl der zurückgegebenen Zeilen beschränkt eine **wählen** Anweisung.  
  
 Zum Ausführen einer Katalogfunktion Ruft eine Anwendung nur die Funktion.  
  
 Weitere Informationen zu Katalogfunktionen, finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).
