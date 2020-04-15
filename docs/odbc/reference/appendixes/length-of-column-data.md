---
title: Länge der Spaltendaten | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- column data [ODBC]
- length of column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: c762c881-ebe0-4eac-84d5-f30281fc3eca
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d0b7ad515661cce4c5b1d407be768cc3da131bb4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304931"
---
# <a name="length-of-column-data"></a>Länge von Spaltendaten
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 Die Cursorbibliothek erstellt einen Puffer im Cache für jeden Längen-/Indikatorpuffer, der mit **SQLBindCol**an das Resultset gebunden ist. Es verwendet die Werte in diesen Puffern, um eine **WHERE-Klausel** zu erstellen, wenn es positionierte Aktualisierungs- oder Löschanweisungen emuliert. Es aktualisiert diese Puffer aus den Rowset-Puffern, wenn Daten aus der Datenquelle abgerufen werden und wenn positionierte Aktualisierungsanweisungen ausgeführt werden.  
  
 Wenn der C-Typ eines Datenpuffers SQL_C_CHAR oder SQL_C_BINARY ist und der Längen-Indikator-Wert SQL_NTS ist, wird die Zeichenfolgenlänge der Daten in den Längen-/Indikatorpuffer eingefügt.  
  
> [!NOTE]  
>  Die Cursorbibliothek aktualisiert ihren Cache für eine Spalte nicht, wenn **StrLen_or_IndPtr* im entsprechenden Rowset-Puffer SQL_DATA_AT_EXEC oder das Ergebnis des SQL_LEN_DATA_AT_EXEC-Makros ist.
