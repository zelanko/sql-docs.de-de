---
title: Puffer | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- input buffers [ODBC]
- length/indicator buffers [ODBC]
- output buffers [ODBC]
- buffers [ODBC], about buffers
- application buffers [ODBC]
- buffers [ODBC]
ms.assetid: 42c5226c-cb40-4d1e-809f-2ea50ce6bd55
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0c49e83e12463665f86f8cc15dc595e6ba2c506f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306285"
---
# <a name="buffers"></a>Puffer
Ein Puffer ist ein beliebiger Anwendungsspeicher, der zum Übergeben von Daten zwischen der Anwendung und dem Treiber verwendet wird. Anwendungspuffer können z. B. **Mit SQLBindCol**zu Ergebnissatzspalten verknüpft oder *an diese gebunden* werden. Wenn jede Zeile abgerufen wird, werden die Daten für jede Spalte in diesen Puffern zurückgegeben. *Eingabepuffer* werden verwendet, um Daten von der Anwendung an den Treiber zu übergeben. *Ausgabepuffer* werden verwendet, um Daten vom Treiber an die Anwendung zurückzugeben.  
  
> [!NOTE]  
>  Wenn eine ODBC-Funktion SQL_ERROR zurückgibt, ist der Inhalt aller Ausgabeargumente für diese Funktion nicht definiert.  
  
 Diese Diskussion beschäftigt sich in erster Linie mit Puffern unbestimmten Typs. Die Adressen dieser Puffer werden als Argumente vom Typ SQLPOINTER angezeigt, z. B. als *TargetValuePtr-Argument* in **SQLBindCol**. Einige der hier beschriebenen Elemente, z. B. die Argumente, die mit Puffern verwendet werden, gelten jedoch auch für Argumente, die zum Übergeben von Zeichenfolgen an den Treiber verwendet werden, z. B. das *TableName-Argument* in **SQLTables**.  
  
 Diese Puffer kommen in der Regel paarweise. *Datenpuffer* werden verwendet, um die Daten selbst zu übergeben, während *Längen-/Indikatorpuffer* verwendet werden, um die Länge der Daten im Datenpuffer oder einen speziellen Wert wie SQL_NULL_DATA zu übergeben, der angibt, dass die Daten NULL sind. Die Länge der Daten in einem Datenpuffer unterscheidet sich von der Länge des Datenpuffers selbst. Die folgende Abbildung zeigt die Beziehung zwischen dem Datenpuffer und dem Längen-/Indikatorpuffer.  
  
 ![Datenpuffer und Länge&#47;Indikatorpuffer](../../../odbc/reference/develop-app/media/pr09.gif "pr09")  
  
 Ein Längen-/Indikatorpuffer ist immer dann erforderlich, wenn der Datenpuffer Daten variabler Länge enthält, z. B. Zeichen- oder Binärdaten. Wenn der Datenpuffer Daten fester Länge enthält, z. B. eine ganze Zahl oder eine Datumsstruktur, wird ein Längen-/Indikatorpuffer nur benötigt, um Indikatorwerte zu übergeben, da die Länge der Daten bereits bekannt ist. Wenn eine Anwendung einen Längen-/Indikatorpuffer mit Daten fester Länge verwendet, ignoriert der Treiber alle darin übergebenen Längen.  
  
 Die Länge des Datenpuffers und der darin enthaltenen Daten wird in Bytes gemessen, im Gegensatz zu Zeichen. Diese Unterscheidung ist für Programme, die ANSI-Zeichenfolgen verwenden, unwichtig, da die Längen in Bytes und Zeichen identisch sind.  
  
 Wenn der Datenpuffer ein treiberdefiniertes Deskriptorfeld, Diagnosefeld oder Attribut darstellt, sollte die Anwendung dem Treiber-Manager die Art des Funktionsarguments angeben, das den Wert für das Feld oder Attribut angibt. Die Anwendung tut dies, indem sie das Length-Argument in jedem Funktionsaufruf festlegt, der das Feld oder Attribut auf einen der folgenden Werte festlegt. (Dasselbe gilt für Funktionen, die die Werte des Felds oder Attributs abrufen, mit der Ausnahme, dass das Argument auf die Werte verweist, die für die Einstellungsfunktion im Argument selbst enthalten sind.)  
  
-   Wenn das Funktionsargument, das den Wert für das Feld oder Attribut angibt, ein Zeiger auf eine Zeichenfolge ist, ist das *Length-Argument* die Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn das Funktionsargument, das den Wert für das Feld oder Attribut angibt, ein Zeiger auf einen Binärpuffer ist, platziert die Anwendung das Ergebnis des*SQL_LEN_BINARY_ATTR(Länge*)-Makros im *Length-Argument.* Dadurch wird ein negativer Wert in das *Length-Argument* platziert.  
  
-   Wenn das Funktionsargument, das den Wert für das Feld oder Attribut angibt, ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder eine Binärzeichenfolge ist, sollte das *Length-Argument* den Wert SQL_IS_POINTER haben.  
  
-   Wenn das Funktionsargument, das den Wert für das Feld oder Attribut angibt, einen Wert mit fester Länge enthält, lautet das *Length-Argument* SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT oder SQL_ISI_USMALLINT.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Zurückgestellte Puffer](../../../odbc/reference/develop-app/deferred-buffers.md)  
  
-   [Zuweisen und Freigeben von Puffern](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)  
  
-   [Verwenden von Datenpuffern](../../../odbc/reference/develop-app/using-data-buffers.md)
