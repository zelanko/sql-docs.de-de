---
description: Ausführen von Katalogfunktionen
title: Ausführen von Katalog Funktionen | Microsoft-Dokumentation
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
ms.openlocfilehash: 19baae1518078c44b8e170fb623eab0087bac12a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482913"
---
# <a name="executing-catalog-functions"></a>Ausführen von Katalogfunktionen
Da eine Katalog Funktion ein Resultset erstellt, entspricht Sie dem Ausführen einer SQL-Anweisung, die ein Resultset generiert. In der Tat werden Katalog Funktionen häufig implementiert, indem vordefinierte SQL-Anweisungen ausgeführt werden oder vordefinierte Prozeduren aufgerufen werden, die mit dem Treiber oder DBMS ausgeliefert werden. Fast alles, was für SQL-Anweisungen gilt, die Resultsets erstellen, gilt auch für Katalog Funktionen. Das Attribut SQL_ATTR_MAX_ROWS Anweisung schränkt beispielsweise die Anzahl der Zeilen ein, die von der Katalog Funktion zurückgegeben werden, ebenso wie die Anzahl der Zeilen, die von einer **Select** -Anweisung zurückgegeben werden.  
  
 Zum Ausführen einer Katalog Funktion Ruft eine Anwendung nur die-Funktion auf.  
  
 Weitere Informationen zu Katalog Funktionen finden Sie unter [Katalog Funktionen](../../../odbc/reference/develop-app/catalog-functions.md).
