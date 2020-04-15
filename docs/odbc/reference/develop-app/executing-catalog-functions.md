---
title: Ausführen von Katalogfunktionen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6469a5394e232ab9d9135fbbbd56ba7b791ccbcb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305721"
---
# <a name="executing-catalog-functions"></a>Ausführen von Katalogfunktionen
Da eine Katalogfunktion ein Resultset erstellt, entspricht dies der Ausführung einer beliebigen SQL-Anweisung zum Generieren von Resultsets. Tatsächlich werden Katalogfunktionen häufig durch Ausführen vordefinierter SQL-Anweisungen oder Aufrufen vordefinierter Prozeduren implementiert, die mit dem Treiber oder DBMS ausgeliefert werden. Fast alles, was für SQL-Anweisungen gilt, die Resultsets erstellen, gilt auch für Katalogfunktionen. Beispielsweise begrenzt das Attribut SQL_ATTR_MAX_ROWS Anweisung die Anzahl der Zeilen, die von der Katalogfunktion zurückgegeben werden, ebenso wie die Anzahl der Zeilen, die von einer **SELECT-Anweisung** zurückgegeben werden.  
  
 Um eine Katalogfunktion auszuführen, ruft eine Anwendung nur die Funktion auf.  
  
 Weitere Informationen zu Katalogfunktionen finden Sie unter [Katalogfunktionen](../../../odbc/reference/develop-app/catalog-functions.md).
