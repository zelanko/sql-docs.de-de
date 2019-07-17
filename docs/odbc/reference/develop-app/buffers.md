---
title: Puffer | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ad13379552e3a5a576b0aa5cc8720ca6ca1688a9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68118742"
---
# <a name="buffers"></a>Puffer
Ein Puffer wird jedem Speicherbereich Anwendung verwendet, um Daten zwischen der Anwendung und den Treiber übergeben. Zum Beispiel Anwendungspuffer zugeordnet sein können, oder *gebunden,* Resultsetspalten mit **SQLBindCol**. Wie jede Zeile abgerufen wird, werden die Daten für jede Spalte in diese Puffer zurückgegeben. *Geben Sie Puffer* werden verwendet, um Daten aus der Anwendung an den Treiber; zu übergeben. *Ausgabepuffer* werden verwendet, um Daten aus dem Treiber des an die Anwendung zurückgegeben.  
  
> [!NOTE]  
>  Wenn eine ODBC-Funktion SQL_ERROR zurückgibt, sind die Inhalte der Ausgabeargumente der Funktion nicht definiert.  
  
 Diese Erläuterung bezieht sich auf sich selbst in erster Linie mit Puffern unbestimmten Typ. Die Adressen der diese Puffer werden als Argumente des Typs SQLPOINTER, z. B. die *TargetValuePtr* -Argument in **SQLBindCol**. Allerdings einige der Elemente, die hier erläutert, wie z. B. die Argumente, mit Puffern, gelten auch für Argumente verwendet, um Zeichenfolgen an den Treiber übergeben, wie z. B. die *TableName* -Argument in **SQLTables**.  
  
 In der Regel treten paarweise auf diese Puffer. *Datenpuffer* werden verwendet, um die Daten selbst zu übergeben, während er sich *Längenindikator/Puffer* werden verwendet, um die Länge der Daten in den Datenpuffer oder ein spezieller Wert wie z. B. SQL_NULL_DATA gibt an, dass die Daten NULL sind übergeben. Die Länge der Daten in einen Datenpuffer unterscheidet sich von der Länge des Datenpuffers selbst. Die folgende Abbildung zeigt die Beziehung zwischen den Datenpuffer und Längen-/Indikatorpuffers.  
  
 ![Datenpuffer und Länge&#47;Indikatorpuffers](../../../odbc/reference/develop-app/media/pr09.gif "pr09")  
  
 Ein Längen-/Indikatorpuffer ist erforderlich, wenn der Datenpuffer Daten mit variabler Länge, wie z. B. Zeichen- oder Binärdaten enthält. Enthält der Datenpuffer-Daten fester Länge, wie z. B. eine ganze Zahl oder Datum-Struktur, ist ein Längen-/Indikatorpuffer nur erforderlich, um Indikatorwerte übergeben werden, da die Länge der Daten bereits bekannt ist. Wenn eine Anwendung ein Längen-/Indikatorpuffer mit fester Länge verwendet wird, ignoriert der Treiber Länge, die sie übergeben.  
  
 Die Länge der sowohl den Datenpuffer und die darin enthaltenen Daten ist in Bytes, im Gegensatz zu Zeichen angegeben. Diese Unterscheidung ist unwichtig für Programme, die ANSI-Zeichenfolgen zu verwenden, da die Länge in Bytes und Zeichen identisch sind.  
  
 Bei der Datenpuffer eine treiberdefinierten Deskriptorfeld, diagnosefeld oder Attribut darstellt, sollte die Anwendung an den Treiber-Manager die Art des Arguments Funktion angeben, der den Wert des Felds oder Attributs angibt. Die Anwendung erledigt dies durch Festlegen der Length-Argument in einem beliebigen Funktionsaufruf, der das Feld oder ein Attribut auf einen der folgenden Werte festgelegt. (Dasselbe gilt für Funktionen, die die Werte des Felds oder Attributs, mit der Ausnahme, die das Argument mit den Werten verweist, die für die Einstellung-Funktion in das Argument selbst sind abrufen.)  
  
-   Wenn das Funktionsargument, die der Wert des Felds oder Attributs gibt an, ein Zeiger auf eine Zeichenfolge, wird die *Länge* -Argument gibt die Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn das Funktionsargument, die der Wert des Felds oder Attributs gibt an, ein Zeiger auf ein binärer Puffer ist, wird die Anwendung platziert das Ergebnis der SQL_LEN_BINARY_ATTR (*Länge*)-Makro in der *Länge* Argument. Dadurch wird einen negativen Wert in der *Länge* Argument.  
  
-   Ist das Funktionsargument, die den Wert des Felds oder Attributs gibt an, ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder eine binäre Zeichenfolge, die *Länge* Argument sollte den Wert SQL_IS_POINTER aufweisen.  
  
-   Wenn das Funktionsargument, die der Wert des Felds oder Attributs gibt an, einen Wert fester Länge enthält die *Länge* Argument ist SQL_IS_INTEGER SQL_IS_UINTEGER, SQL_IS_SMALLINT oder SQL_ISI_USMALLINT, nach Bedarf.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Verzögerte Puffer](../../../odbc/reference/develop-app/deferred-buffers.md)  
  
-   [Zuweisen und Freigeben von Puffern](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)  
  
-   [Verwenden von Datenpuffern](../../../odbc/reference/develop-app/using-data-buffers.md)
