---
title: Spaltendaten | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 0425818c-9469-493f-9e3c-fc03d9411c5c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ff89566efa65c88325d98422fe17788f27d2c8ca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306591"
---
# <a name="column-data"></a>Spaltendaten
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 Die Cursorbibliothek erstellt einen Puffer im Cache für jeden Datenpuffer, der mit **SQLBindCol**an das Resultset gebunden ist. Es verwendet die Werte in diesen Puffern, um eine **WHERE-Klausel** zu erstellen, wenn eine positionierte Aktualisierungs- oder Löschanweisung emuliert wird. Es aktualisiert diese Puffer aus den Rowset-Puffern, wenn Daten aus der Datenquelle abgerufen werden und wenn positionierte Aktualisierungsanweisungen ausgeführt werden.  
  
 Wenn die Cursorbibliothek ihren Cache aus den Rowsetpuffern aktualisiert, werden die Daten gemäß dem in **SQLBindCol**angegebenen C-Datentyp übertragen. Wenn z. B. der C-Datentyp eines Rowsetpuffers SQL_C_SLONG ist, überträgt die Cursorbibliothek vier Byte Daten. Wenn es SQL_C_CHAR und *BufferLength* 10 ist, überträgt die Cursorbibliothek 10 Byte Daten. Die Cursorbibliothek führt keine Typüberprüfungen oder Konvertierungen für die übertragenen Daten durch.  
  
> [!NOTE]  
>  Die Cursorbibliothek aktualisiert ihren Cache für eine Spalte nicht, wenn **StrLen_or_IndPtr* im entsprechenden Rowset-Puffer SQL_DATA_AT_EXEC oder das Ergebnis des SQL_LEN_DATA_AT_EXEC-Makros ist.  
  
 Wenn eine Spalte aktualisiert wird, werden bei Bedarf eine Datenquelle mit leeren Pads mit Zeichendaten fester Länge und Binärdaten mit fester Länge mit fester Länge aufeinem Feld gesetzt. Eine Datenquelle speichert beispielsweise "Smith" in einer CHAR(10)-Spalte als "Smith ". Die Cursorbibliothek enthält keine Leerpad- oder Null-Pad-Daten in den Rowset-Puffern, wenn sie diese Daten nach dem Ausführen einer positionierten Update-Anweisung in ihren Cache kopiert. Wenn eine Anwendung erfordert, dass die Werte im Cache der Cursorbibliothek leer gepolstert oder mit Null gepolstert sind, muss sie daher die Werte in den Rowset-Puffern leer oder null padieren, bevor eine positionierte Update-Anweisung ausgeführt wird.
