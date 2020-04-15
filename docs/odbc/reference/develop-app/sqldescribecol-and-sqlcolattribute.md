---
title: SQLDescribeCol und SQLColAttribute | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], and SQLDescribeCol
- SQLDescribeCol function [ODBC], and SQLColAttribute
- result sets [ODBC], metadata
- retrieving result set meta data [ODBC]
- metadata [ODBC], result set
ms.assetid: c2ca442c-03a8-4e0f-9e67-b300bb15962f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8bd21010908473e4216a02a504b2de25578d5c84
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299760"
---
# <a name="sqldescribecol-and-sqlcolattribute"></a>SQLDescribeCol und SQLColAttribute
**SQLDescribeCol** und **SQLColAttribute** werden zum Abrufen von Resultsetmetadaten verwendet. Der Unterschied zwischen diesen beiden Funktionen besteht darin, dass **SQLDescribeCol** immer dieselben fünf Informationen zurückgibt (Name, Datentyp, Genauigkeit, Skalierung und Nullbarkeit einer Spalte), während **SQLColAttribute** eine einzelne Information zurückgibt, die von der Anwendung angefordert wird. **SQLColAttribute** kann jedoch eine viel umfangreichere Auswahl an Metadaten zurückgeben, einschließlich der Groß-/Kleinschreibung, der Anzeigegröße, der Aufkläsbarkeit und der Durchsuchbarkeit einer Spalte.  
  
 Viele Anwendungen, insbesondere Anwendungen, die nur Daten anzeigen, erfordern nur die Metadaten, die von **SQLDescribeCol**zurückgegeben werden. Bei diesen Anwendungen ist die Verwendung von **SQLDescribeCol** schneller als **SQLColAttribute,** da die Informationen in einem einzelnen Aufruf zurückgegeben werden. Andere Anwendungen, insbesondere Anwendungen, die Daten aktualisieren, erfordern die zusätzlichen Metadaten, die von **SQLColAttribute** zurückgegeben werden, und verwenden daher beide Funktionen. Darüber hinaus unterstützt **SQLColAttribute** treiberspezifische Metadaten. Weitere Informationen finden Sie unter [Treiberspezifische Datentypen, Deskriptortypen, Informationstypen, Diagnosetypen und Attribute](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Eine Anwendung kann Resultsetmetadaten jederzeit abrufen, nachdem eine Anweisung vorbereitet oder ausgeführt wurde und bevor der Cursor über dem Resultset geschlossen wird. Nur sehr wenige Anwendungen benötigen Metadaten für die Ergebnismenge, nachdem die Anweisung vorbereitet und ausgeführt wurde. Wenn möglich, sollten Anwendungen warten, bis Metadaten abgerufen werden, bis die Anweisung ausgeführt wurde, da einige Datenquellen keine Metadaten für vorbereitete Anweisungen zurückgeben können und das Emulieren dieser Funktion im Treiber häufig ein langsamer Prozess ist. Der Treiber kann z. B. ein Ergebnissatz mit null Zeilen generieren, indem er die **WHERE-Klausel** einer **SELECT-Anweisung** durch die Klausel **WHERE 1 = 2** ersetzt und die resultierende Anweisung ausführt.  
  
 Das Abrufen von Metadaten aus der Datenquelle ist häufig teuer. Aus diesem Grund sollten Treiber alle Metadaten zwischenspeichern, die sie vom Server abrufen, und sie so lange halten, wie der Cursor über dem Resultset geöffnet ist. Außerdem sollten Anwendungen nur die Metadaten anfordern, die sie unbedingt benötigen.
