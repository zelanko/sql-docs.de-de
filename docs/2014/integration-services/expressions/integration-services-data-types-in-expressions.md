---
title: Integration Services-Datentypen in Ausdrücken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- expressions [Integration Services], data types
- data types [Integration Services], expressions
ms.assetid: c296ad10-4080-4988-8c2c-2c250f7a1884
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 80110c29ec1c576684c4ccd67bc0c3408e6250b3
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53363343"
---
# <a name="integration-services-data-types-in-expressions"></a>Integration Services-Datentypen in Ausdrücken
  Die Ausdrucksauswertung verwendet [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Datentypen. Wenn Daten erstmals an einen Datenfluss in einem [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Paket weitergegeben werden, konvertiert die Datenfluss-Engine alle Spaltendaten in einen [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Datentyp, und die von einem Ausdruck verwendeten Spaltendaten weisen bereits einen [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Datentyp auf. Ausdrücke, die in den Transformationen für bedingtes Teilen und für abgeleitete Spalten verwendet werden, können auf Spalten verweisen, weil sie Teil eines Datenflusses mit Spaltendaten sind.  
  
## <a name="variables"></a>Variablen  
 In Ausdrücken können außerdem Variablen verwendet werden. Variablen weisen einen Variant-Datentyp auf, und die Ausdrucksauswertung konvertiert den Datentyp einer Variablen von einem Variant-Untertyp in einen [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Datentyp, bevor der Ausdruck ausgewertet wird. Für Variablen kann nur eine Teilmenge der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Datentypen verwendet werden. Beispielsweise ist für eine Variable kein BLOB-Datentyp (Binary Large Object Block) zulässig.  
  
 Weitere Informationen zu [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Datentypen und zum Zuordnen von Variant-Datentypen zu [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Datentypen finden Sie unter [Integration Services-Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="literals"></a>Literale  
 Darüber hinaus können Ausdrücke numerische und boolesche Literale sowie Zeichenfolgenliterale einschließen. Weitere Informationen zum Konvertieren von numerischen Literalen in numerische [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Datentypen finden Sie unter [Literale &#40;SSIS&#41;](numeric-string-and-boolean-literals.md).  
  
## <a name="implicit-data-conversion"></a>Implizite Datenkonvertierung  
 Bei einer impliziten Datentypkonvertierung konvertiert die Ausdrucksauswertung die Daten automatisch in einen anderen Datentyp. Beispielsweise wird beim Vergleich eines `smallint`-Datentyps mit einem `int`-Datentyp der `smallint`-Datentyp implizit in `int` konvertiert, bevor der Vergleich ausgeführt wird.  
  
 Wenn die Argumente und Operanden nicht kompatible Datentypen aufweisen, kann die Ausdrucksauswertung keine implizite Datenkonvertierung ausführen. Zudem kann die Ausdrucksauswertung einen Wert nicht implizit in einen booleschen Wert konvertieren. Stattdessen müssen die Argumente und Operanden explizit mit dem Umwandlungsoperator konvertiert werden. Weitere Informationen finden Sie unter [Umwandlung &#40;SSIS-Ausdruck&#41;](cast-ssis-expression.md).  
  
 Das folgende Diagramm zeigt den Ergebnistyp impliziter Konvertierungen von BINARY-Vorgängen. Am Schnittpunkt von Spalte und Zeile in dieser Tabelle finden Sie den Ergebnistyp einer binären Operation mit Operanden der Typen, die links (Von) und rechts (Zu) angegeben sind.  
  
 ![Implizite Datentypkonvertierung zwischen Datentypen](../media/mw-dts-impl-conver-02.gif "Implizite Datentypkonvertierung zwischen Datentypen")  
  
 Die Schnittmenge eines integer-Werts mit Vorzeichen und eines integer-Werts ohne Vorzeichen ist ein integer-Wert, der potenziell größer als die beiden Argumente ist.  
  
 Anhand von Operatoren werden Zeichenfolgen, Datumsangaben, boolesche Werte und andere Datentypen miteinander verglichen. Bevor ein Operator zwei Werte vergleicht, führt die Ausdrucksauswertung bestimmte implizite Konvertierungen aus: Die Ausdrucksauswertung konvertiert Zeichenfolgenliterale stets in den DT_WSTR-Datentyp und boolesche Literale in den DT_BOOL-Datentyp. Alle in Anführungszeichen eingeschlossenen Werte werden von der Ausdrucksauswertung als Zeichenfolgen interpretiert. Numerische Literale werden in einen der numerischen [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Datentypen konvertiert.  
  
> [!NOTE]  
>  Boolesche Werte sind keine Zahlen, sondern logische Werte. Obwohl einige Umgebungen boolesche Werte als Zahlenwerte darstellen, werden Sie nicht als Zahlen gespeichert. Je nach Programmiersprache werden boolesche Werte als unterschiedliche Zahlenwerte dargestellt. Dies gilt auch für .NET Framework-Methoden.  
>   
>  Beispielsweise konvertieren die Konvertierungsfunktionen von Visual Basic den Wert `True` in den Zahlenwert -1. Die `System.Convert.ToInt32`-Methode von .NET Framework konvertiert den Wert `True` jedoch in den Zahlenwert +1. In der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Ausdruckssprache wird der Wert `True` in den Zahlenwert -1 konvertiert.  
>   
>  Um Fehler oder unerwartete Ergebnisse zu vermeiden, sollten Sie keinen Code erstellen, der von bestimmten numerischen Werten für `True` und `False` abhängig ist. Nach Möglichkeit sollten bei booleschen Variablen nur die für sie vorgesehenen logischen Werte verwendet werden.  
  
 Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [== &#40;Gleich&#41; &#40;SSIS-Ausdruck&#41;](equal-ssis-expression.md)  
  
-   [\!= &#40;Ungleich&#41; &#40;SSIS-Ausdruck&#41;](unequal-ssis-expression.md)  
  
-   [&#62; &#40;Größer als&#41; &#40;SSIS-Ausdruck&#41;](greater-than-ssis-expression.md)  
  
-   [&#60; &#40;Kleiner als&#41; &#40;SSIS-Ausdruck&#41;](less-than-ssis-expression.md)  
  
-   [&#62;= &#40;Größer oder gleich&#41; &#40;SSIS-Ausdruck&#41;](greater-than-or-equal-to-ssis-expression.md)  
  
-   [&#60;= &#40;Kleiner oder gleich&#41; &#40;SSIS-Ausdruck&#41;](less-than-or-equal-to-ssis-expression.md)  
  
 Eine Funktion mit einem einzelnen Argument gibt ein Ergebnis mit dem Datentyp des Arguments zurück, wobei folgende Ausnahmen gelten:  
  
-   DAY, MONTH und YEAR akzeptieren ein Datum und geben ein ganzzahliges Ergebnis (DT_I4) zurück.  
  
-   ISNULL akzeptiert einen Ausdruck eines beliebigen [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Datentyps und gibt einen booleschen Datentyp (DT_BOOL) zurück.  
  
-   SQUARE und SQRT akzeptieren einen numerischen Ausdruck und geben ein nicht integrales numerisches (DT_R8) Ergebnis zurück.  
  
 Falls die Argumente vom gleichen Datentyp sind, gehört auch das Ergebnis zu diesem Datentyp. Die einzige Ausnahme ist das Ergebnis einer binären Operation für zwei Werte mit dem DT_DECIMAL-Datentyp. In diesem Fall wird ein Ergebnis mit dem DT_NUMERIC-Datentyp zurückgegeben.  
  
## <a name="requirements-for-data-used-in-expressions"></a>Voraussetzungen für die Verwendung von Daten in Ausdrücken  
 Die Ausdrucksauswertung unterstützt alle [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Datentypen. Je nach Operation oder Funktion sind jedoch für die Operanden und Argumente bestimmte Datentypen erforderlich. Die Ausdrucksauswertung erzwingt die folgenden Datentypanforderungen für Daten, die in Ausdrücken verwendet werden:  
  
-   Operanden, die in **logischen** Operationen verwendet werden, müssen zu einem booleschen Wert ausgewertet werden. Beispiel: COLUMNA > 1&&COLUMNB < 2.  
  
-   Operanden, die in **mathematischen** Operationen verwendet werden, müssen zu einem numerischen Wert ausgewertet werden. Beispiel: 23.75 * 4.  
  
-   In Vergleichsoperationen, z. B. logischen und Gleichheitsoperationen, verwendete Operanden müssen zu kompatiblen Datentypen ausgewertet werden.  
  
     In einem der Ausdrücke im folgenden Beispiel wird z. B. der DT_DBTIMESTAMPOFFSET-Datentyp verwendet:  
  
     `(DT_DBTIMESTAMPOFFSET,3) "1999-10-11 20:34:52.123 -3:30" != (DT_DBDATE)"1999-10-12"`  
  
     Der Ausdruck `(DT_DBDATE)"1999-10-12"`wird in DT_DBTIMESTAMPOFFSET konvertiert. In diesem Beispiel wird zu TRUE ausgewertet, weil der konvertierte Ausdruck zu "1999-10-12 00:00:00.000 +00:00" wird, was nicht dem Wert des anderen Ausdrucks entspricht, der `(DT_DBTIMESTAMPOFFSET,3) "1999-10-11 20:34:52.123 -3:30"`lautet.  
  
-   Argumente, die an mathematische Funktionen übergeben werden, müssen zu einem numerischen Datentyp ausgewertet werden. Je nach Funktion oder Operation kann ein bestimmter numerischer Datentyp erforderlich sein. Beispielsweise erfordert die HEX-Funktion eine ganze Zahl mit oder ohne Vorzeichen.  
  
-   Argumente, die an Zeichenfolgenfunktionen übergeben müssen zu einem Zeichendatentyp ausgewertet: DT_STR oder DT_WSTR. Beispiel: UPPER("flower"). Manche Zeichenfolgenfunktionen, wie z. B. SUBSTRING, erfordern zusätzliche ganzzahlige Argumente für die Startposition und die Länge der Zeichenfolge.  
  
-   Argumente, die an Datums- und Zeitfunktionen übergeben werden, müssen zu einem gültigen Datum ausgewertet werden. Beispielsweise DAY(GETDATE()). Manche Funktionen, wie z. B. DATEADD, erfordern ein zusätzliches ganzzahliges Argument für die Anzahl von Tagen, die von der Funktion zu einem Datum addiert werden.  
  
 Für Operationen, bei denen ein integer-Wert ohne Vorzeichen mit der Länge von 8 Byte und ein integer-Wert mit Vorzeichen kombiniert werden, ist zum Klären des Ergebnisformats eine explizite Umwandlung erforderlich. Weitere Informationen finden Sie unter [Umwandlung &#40;SSIS-Ausdruck&#41;](cast-ssis-expression.md).  
  
 Die Ergebnisse vieler Operationen und Funktionen können vordefinierte Datentypen aufweisen. Dies kann der Datentyp des Arguments oder der Datentyp sein, in den die Ausdrucksauswertung das Ergebnis umwandelt. Beispielsweise ist das Ergebnis eines logischen OR-Operators (||) immer ein boolescher Wert, das Ergebnis der ABS-Funktion ist der numerische Datentyp des Arguments, und das Ergebnis einer Multiplikation ist der kleinste numerische Datentyp, der das Ergebnis ohne Verlust speichern kann. Weitere Informationen zu den Datentypen von Ergebnissen finden Sie unter [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md) und [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 [Verwenden eines Ausdrucks in einer Datenflusskomponente](../use-an-expression-in-a-data-flow-component.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   Technischer Artikel, [SSIS Expression Cheat Sheet](https://go.microsoft.com/fwlink/?LinkId=217683), auf pragmaticworks.com  
  
-   Technischer Artikel, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), auf social.technet.microsoft.com  
  
  
