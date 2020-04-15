---
title: Argumentwertprüfungen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- argument value checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 37a65f8b-83aa-456c-b7cf-500404abb38a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6c6e4de16c4a1a80be893acbc7a1993b375f2fee
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298822"
---
# <a name="argument-value-checks"></a>Überprüfungen des Argumentwerts
Der Treiber-Manager überprüft die folgenden Argumentetypen. Sofern nicht anders angegeben, gibt der Treiber-Manager SQL_ERROR für Fehler in Argumentwerten zurück.  
  
-   Umgebungs-, Verbindungs- und Anweisungshandles können in der Regel keine NULL-Zeiger sein. Der Treiber-Manager gibt SQL_INVALID_HANDLE zurück, wenn er ein NULL-Handle findet.  
  
-   Erforderliche Zeigerargumente, z. B. *OutputHandlePtr* in **SQLAllocHandle** und *CursorName* in **SQLSetCursorName**, können keine NULLzeiger sein.  
  
-   Optionsflags, die keine treiberspezifischen Werte unterstützen, müssen ein rechtlicher Wert sein. Der *Vorgang* in **SQLSetPos** muss z. B. SQL_POSITION, SQL_REFRESH, SQL_UPDATE, SQL_DELETE oder SQL_ADD sein.  
  
-   Optionsflags müssen in der vom Treiber unterstützten ODBC-Version unterstützt werden. Beispielsweise kann *InfoType* in **SQLGetInfo** beim Aufrufen eines ODBC 2.0-Treibers nicht SQL_ASYNC_MODE (in ODBC 3.0) eingeführt werden.  
  
-   Spalten- und Parameternummern müssen je nach Funktion größer als 0 oder größer oder gleich 0 sein. Der Treiber muss die Obergrenze dieser Argumentwerte basierend auf dem aktuellen Resultset oder der SQL-Anweisung überprüfen.  
  
-   Länge/Indikator-Argumente und Datenpufferlängenargumente müssen geeignete Werte enthalten. Beispielsweise muss das Argument, das die Länge eines Tabellennamens in **SQLColumns** (*NameLength3*) angibt, SQL_NTS oder ein Wert größer als 0 sein. *BufferLength* in **SQLDescribeCol** muss größer oder gleich 0 sein. Möglicherweise muss der Treiber auch diese Argumente überprüfen. Es kann z. B. überprüft werden, ob *NameLength3* kleiner oder gleich der maximalen Länge eines Tabellennamens in der Datenquelle ist.
