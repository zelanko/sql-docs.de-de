---
title: Argument Wert Überprüfungen | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298822"
---
# <a name="argument-value-checks"></a>Überprüfungen des Argumentwerts
Der Treiber-Manager überprüft die folgenden Argument Typen. Sofern nicht anders angegeben, gibt der Treiber-Manager SQL_ERROR für Fehler in Argument Werten zurück.  
  
-   Umgebungs-, Verbindungs-und Anweisungs Handles dürfen in der Regel keine NULL-Zeiger sein. Der Treiber-Manager gibt SQL_INVALID_HANDLE zurück, wenn er ein NULL-Handle findet.  
  
-   Erforderliche Zeigerargumente, z. b. *outputhandleptr* in **sqlzuzugchandle** und *Cursor Name* in **sqlsetcursor Name**, dürfen keine NULL-Zeiger sein.  
  
-   Optionsflags, die keine treiberspezifischen Werte unterstützen, müssen ein gültiger Wert sein. Der *Vorgang* in **SQLSetPos** muss z. b. SQL_POSITION, SQL_REFRESH, SQL_UPDATE, SQL_DELETE oder SQL_ADD sein.  
  
-   Optionsflags müssen in der Version von ODBC unterstützt werden, die vom Treiber unterstützt wird. Beispielsweise kann *InfoType* in **SQLGetInfo** nicht SQL_ASYNC_MODE (eingeführt in ODBC 3,0), wenn ein ODBC 2,0-Treiber aufgerufen wird.  
  
-   Die Spalten-und Parameter Nummern müssen abhängig von der Funktion größer als 0 (null) oder größer oder gleich 0 sein. Der Treiber muss die Obergrenze dieser Argument Werte basierend auf dem aktuellen Resultset oder der SQL-Anweisung überprüfen.  
  
-   Längen-/indikatorargumente und Datenpuffer Längen-Argumente müssen geeignete Werte enthalten. Beispielsweise muss das Argument, das die Länge eines Tabellennamens in **SQLColumns** (*NameLength3*) angibt, SQL_NTS oder ein Wert größer als 0 sein. *BufferLength* in **SQLDescribeCol** muss größer oder gleich 0 sein. Der Treiber muss möglicherweise auch diese Argumente überprüfen. Beispielsweise kann überprüft werden, ob *NameLength3* kleiner oder gleich der maximalen Länge eines Tabellennamens in der Datenquelle ist.
