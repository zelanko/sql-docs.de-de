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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68118742"
---
# <a name="buffers"></a>Puffer
Ein Puffer ist ein beliebiger Teil des Anwendungs Speichers, der verwendet wird, um Daten zwischen der Anwendung und dem Treiber zu übergeben. Anwendungs Puffer können z. b. Resultsetspalten mit **SQLBindCol**verknüpft oder *an diese gebunden* werden. Wenn jede Zeile abgerufen wird, werden die Daten für jede Spalte in diesen Puffern zurückgegeben. *Eingabepuffer* werden verwendet, um Daten von der Anwendung an den Treiber zu übergeben. *Ausgabepuffer* werden verwendet, um Daten vom Treiber an die Anwendung zurückzugeben.  
  
> [!NOTE]  
>  Wenn eine ODBC-Funktion SQL_ERROR zurückgibt, ist der Inhalt aller Ausgabe Argumente für diese Funktion nicht definiert.  
  
 Diese Erörterung bezieht sich hauptsächlich auf Puffer mit unbestimmtem Typ. Die Adressen dieser Puffer werden als Argumente des Typs SQLPOINTER angezeigt, z. b. das *targetvalueptr* -Argument in **SQLBindCol**. Einige der hier erörterten Elemente, wie z. b. die mit Puffern verwendeten Argumente, gelten jedoch auch für Argumente, die zum Übergeben von Zeichen folgen an den Treiber verwendet werden, wie z. b. das *TableName* -Argument in **SQLTables**.  
  
 Diese Puffer treten in der Regel paarweise auf. *Datenpuffer* werden verwendet, um die Daten selbst zu übergeben, während *Längen-/Indikatorpuffer* verwendet werden, um die Länge der Daten im Datenpuffer oder einen speziellen Wert, wie z. b. SQL_NULL_DATA, zu übergeben, was darauf hinweist, dass die Daten NULL sind. Die Länge der Daten in einem Datenpuffer unterscheidet sich von der Länge des Daten Puffers selbst. Die folgende Abbildung zeigt die Beziehung zwischen dem Datenpuffer und dem length/Indicator-Puffer.  
  
 ![Datenpuffer-und Längen&#47;Indikator Puffer](../../../odbc/reference/develop-app/media/pr09.gif "pr09")  
  
 Ein Längen-/Indikatorpuffer ist immer dann erforderlich, wenn der Datenpuffer Daten variabler Länge enthält, z. b. Zeichen-oder Binärdaten. Wenn der Datenpuffer Daten fester Länge enthält, z. b. eine ganzzahlige oder eine Datums Struktur, ist ein Längen-/Indikatorpuffer nur erforderlich, um Indikatorwerte zu übergeben, da die Länge der Daten bereits bekannt ist. Wenn eine Anwendung einen Längen-/indikatorenpuffer mit Daten fester Länge verwendet, ignoriert der Treiber alle übergebenen Längen.  
  
 Die Länge des Daten Puffers und der darin enthaltenen Daten wird in Byte gemessen (im Gegensatz zu Zeichen). Dieser Unterschied ist für Programme, die ANSI-Zeichen folgen verwenden, unerheblich, da Längen in Bytes und Zeichen identisch sind.  
  
 Wenn der Datenpuffer ein Treiber definiertes Deskriptorfeld, ein Diagnose Feld oder ein ungültiges Attribut darstellt, sollte die Anwendung dem Treiber-Manager die Art des Funktionsarguments geben, das den Wert für das Feld oder Attribut angibt. Die Anwendung bewirkt dies, indem das length-Argument in jedem Funktions Aufrufsatz festgelegt wird, der das Feld oder Attribut auf einen der folgenden Werte festlegt. (Gleiches gilt für Funktionen, die die Werte des Felds oder Attributs abrufen, mit der Ausnahme, dass das-Argument auf die Werte zeigt, die für die Setting-Funktion im Argument selbst sind.)  
  
-   Wenn das Funktions Argument, das den Wert für das Feld oder das Attribut angibt, ein Zeiger auf eine Zeichenfolge ist, entspricht das *length* -Argument der Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn das Funktions Argument, das den Wert für das Feld oder das Attribut angibt, ein Zeiger auf einen binären Puffer ist, platziert die Anwendung das Ergebnis des SQL_LEN_BINARY_ATTR (*length*)-Makros im *length* -Argument. Dadurch wird ein negativer Wert in das *length* -Argument eingefügt.  
  
-   Wenn das Funktions Argument, das den Wert für das Feld oder Attribut angibt, ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder eine binäre Zeichenfolge ist, sollte das *length* -Argument den Wert SQL_IS_POINTER haben.  
  
-   Wenn das Funktions Argument, das den Wert für das Feld oder das Attribut angibt, einen Wert mit fester Länge enthält, wird das *length* -Argument entsprechend SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT oder SQL_ISI_USMALLINT.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Zurückgestellte Puffer](../../../odbc/reference/develop-app/deferred-buffers.md)  
  
-   [Zuweisen und Freigeben von Puffern](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)  
  
-   [Verwenden von Datenpuffern](../../../odbc/reference/develop-app/using-data-buffers.md)
