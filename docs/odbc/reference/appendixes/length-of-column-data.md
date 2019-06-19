---
title: Länge der Spaltendaten | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d14fa4303dd1f67a77bf14dcebeeb933ccce9e1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188826"
---
# <a name="length-of-column-data"></a>Länge von Spaltendaten
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 Die Cursorbibliothek erstellt einen Puffer in den Cache für jede an das Resultset mit gebundenen Längen-/Indikatorpuffer **SQLBindCol**. Er verwendet die Werte in diesen Puffern zum Erstellen einer **, in denen** -Klausel, wenn es emuliert positioniertes Update oder delete-Anweisungen. Diese Puffer von den Puffern Rowset aktualisiert, wenn er ruft Daten aus der Datenquelle und die Ausführung der positionierte Update-Anweisungen ab.  
  
 Wenn der C-Typ, der einen Datenpuffer SQL_C_CHAR oder sql_c_binary angegeben ist und der Längenindikator /-Wert SQL_NTS ist, wird die Länge der Zeichenfolge der Daten in den Längen-/Indikatorpuffer versetzt.  
  
> [!NOTE]  
>  Die Cursorbibliothek nicht seinem Cache nach einer Spalte aktualisiert, wenn **StrLen_or_IndPtr* in das entsprechende Rowset Puffer SQL_DATA_AT_EXEC oder das Ergebnis des Makros SQL_LEN_DATA_AT_EXEC ist.
