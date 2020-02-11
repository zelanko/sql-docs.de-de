---
title: SQLDescribeCol und SQLColAttribute | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d602368475c6f1326cc615453116e898b1c1892f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107442"
---
# <a name="sqldescribecol-and-sqlcolattribute"></a>SQLDescribeCol und SQLColAttribute
**SQLDescribeCol** und **SQLColAttribute** werden zum Abrufen von Resultsetmetadaten verwendet. Der Unterschied zwischen diesen beiden Funktionen besteht darin, dass **SQLDescribeCol** immer dieselben fünf Informationen zurückgibt (Spaltenname, Datentyp, Genauigkeit, Dezimalstelle und NULL-Zulässigkeit), während **SQLColAttribute** ein einzelnes Informationselement zurückgibt, das von der Anwendung angefordert wird. **SQLColAttribute** kann jedoch eine viel umfassendere Auswahl von Metadaten zurückgeben, einschließlich der Berücksichtigung der Groß-/Kleinschreibung, der Anzeige Größe, der Aktualisierbarkeit und der Suchbarkeit.  
  
 Viele Anwendungen, insbesondere solche, die nur Daten anzeigen, erfordern nur die von **SQLDescribeCol**zurückgegebenen Metadaten. Für diese Anwendungen ist es schneller, **SQLDescribeCol** als **SQLColAttribute** zu verwenden, da die Informationen in einem einzelnen-Befehl zurückgegeben werden. Andere Anwendungen, insbesondere solche, die Daten aktualisieren, erfordern die zusätzlichen Metadaten, die von **SQLColAttribute** zurückgegeben werden, und verwenden daher beide Funktionen. Außerdem unterstützt **SQLColAttribute** Treiber spezifische Metadaten. Weitere Informationen finden Sie unter [Treiber spezifische Datentypen, deskriptortypen, Informationstypen, Diagnose Typen und Attribute](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Eine Anwendung kann die Resultsetmetadaten jederzeit abrufen, nachdem eine Anweisung vorbereitet oder ausgeführt wurde und bevor der Cursor über dem Resultset geschlossen wird. Nur wenige Anwendungen benötigen Resultsetmetadaten, nachdem die-Anweisung vorbereitet wurde und bevor Sie ausgeführt wird. Wenn möglich, sollten Anwendungen auf das Abrufen von Metadaten warten, bis die Ausführung der Anweisung erfolgt ist, weil einige Datenquellen keine Metadaten für vorbereitete Anweisungen zurückgeben können und das emuinieren dieser Funktion im Treiber häufig einen langsamen Prozess ist. Beispielsweise generiert der Treiber möglicherweise ein Resultset mit null Zeilen, indem die **Where** -Klausel einer **Select** -Anweisung durch die-Klausel ersetzt wird, **wobei 1 = 2** und die resultierende-Anweisung ausgeführt wird.  
  
 Metadaten sind häufig aufwendig, um aus der Datenquelle abzurufen. Aus diesem Grund sollten Treiber alle Metadaten Zwischenspeichern, die Sie vom Server abrufen, und Sie speichern, solange der Cursor über dem Resultset geöffnet ist. Außerdem sollten Anwendungen nur die erforderlichen Metadaten anfordern.
