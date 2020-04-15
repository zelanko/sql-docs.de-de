---
title: SELECT - SQL-Befehl | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- select [ODBC]
ms.assetid: 2149c3ca-3a71-446d-8d53-3d056e2f301a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 640189a5a31d0c21642b037e906bd6361690a9a5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300940"
---
# <a name="select---sql-command"></a>SELECT (SQL-Befehl)
Ruft Daten aus einer oder mehreren Tabellen ab.  
  
 Der Visual FoxPro ODBC-Treiber unterstützt die native Visual FoxPro-Sprachsyntax für diesen Befehl. Treiberspezifische Informationen finden Sie unter **Treiberhinweise**.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SELECT [ALL | DISTINCT]  
   [Alias.] Select_Item [AS Column_Name]  
   [, [Alias.] Select_Item [AS Column_Name] ...]   
FROM [DatabaseName!]Table [Local_Alias]  
   [, [DatabaseName!]Table [Local_Alias] ...]   
[WHERE JoinCondition [AND JoinCondition  
...]  
   [AND | OR FilterCondition [AND | OR FilterCondition ...]]]  
[GROUP BY GroupColumn [, GroupColumn ...]]  
[HAVING FilterCondition]  
[UNION [ALL] SELECTCommand]  
[ORDER BY Order_Item [ASC | DESC] [, Order_Item [ASC | DESC] ...]]  
```  
  
## <a name="arguments"></a>Argumente  
  
> [!NOTE]  
>  Eine *Unterabfrage*, auf die in den folgenden Argumenten verwiesen wird, ist ein SELECT innerhalb eines SELECT und muss in Klammern eingeschlossen werden. Sie können bis zu zwei Unterabfragen auf derselben Ebene (nicht geschachtelt) in der WHERE-Klausel haben. (Siehe diesen Abschnitt der Argumente.) Unterabfragen können mehrere Verknüpfungsbedingungen enthalten.  
  
 [ALLE &#124; DISTINCT]   [*Alias*.] *Select_Item* [AS *Column_Name*] [,*[Alias*.] *Select_Item* [AS *Column_Name*] ...]  
 Die SELECT-Klausel gibt die Felder, Konstanten und Ausdrücke an, die in den Abfrageergebnissen angezeigt werden.  
  
 Standardmäßig zeigt ALL alle Zeilen in den Abfrageergebnissen an.  
  
 DISTINCT schließt Duplikate von Zeilen aus den Abfrageergebnissen aus.  
  
> [!NOTE]  
>  Sie können DISTINCT nur einmal pro SELECT-Klausel verwenden.  
  
 *Alias*. qualifiziert übereinstimmende Elementnamen. Jedes Element, das Sie mit *Select_Item* angeben, generiert eine Spalte der Abfrageergebnisse. Wenn zwei oder mehr Elemente denselben Namen haben, schließen Sie den Tabellenalias und einen Punkt vor dem Elementnamen ein, um zu verhindern, dass Spalten dupliziert werden.  
  
 *Select_Item* gibt ein Element an, das in die Abfrageergebnisse einbezogen werden soll. Ein Element kann einer der folgenden sein:  
  
-   Der Name eines Felds aus einer Tabelle in der FROM-Klausel.  
  
-   Eine Konstante, die angibt, dass derselbe Konstantenwert in jeder Zeile der Abfrageergebnisse angezeigt werden soll.  
  
-   Ein Ausdruck, der der Name einer benutzerdefinierten Funktion sein kann.  
  
 **Benutzerdefinierte Funktionen mit SELECT**  
  
 Obwohl die Verwendung benutzerdefinierter Funktionen in der SELECT-Klausel offensichtliche Vorteile hat, sollten Sie auch die folgenden Einschränkungen berücksichtigen:  
  
-   Die Geschwindigkeit der mit SELECT ausgeführten Vorgänge kann durch die Geschwindigkeit begrenzt werden, mit der solche benutzerdefinierten Funktionen ausgeführt werden. Manipulationen mit hohem Volumen mit benutzerdefinierten Funktionen können möglicherweise besser durch die Verwendung von API- und benutzerdefinierten Funktionen in C- oder Assemblysprache durchgeführt werden.  
  
-   Die einzige zuverlässige Möglichkeit, Werte an benutzerdefinierte Funktionen zu übergeben, die von SELECT aufgerufen werden, ist die Argumentliste, die an die Funktion übergeben wird, wenn sie aufgerufen wird.  
  
-   Selbst wenn Sie experimentieren und eine angeblich verbotene Manipulation entdecken, die in einer bestimmten Version von FoxPro korrekt funktioniert, gibt es keine Garantie, dass sie in späteren Versionen weiterfunktioniert.  
  
 Abgesehen von diesen Einschränkungen sind benutzerdefinierte Funktionen in der SELECT-Klausel akzeptabel. Denken Sie jedoch daran, dass die Verwendung von SELECT die Leistung beeinträchtigen kann.  
  
 Die folgenden Feldfunktionen stehen für die Verwendung mit einem ausgesuchten Element zur Verfügung, das ein Feld oder ein Ausdruck mit einem Feld ist:  
  
-   AVG(*Select_Item*)-Durchschnittlich eine Spalte mit numerischen Daten.  
  
-   COUNT(*Select_Item*)-Zählt die Anzahl der ausgewählten Elemente in einer Spalte. COUNT(*) zählt die Anzahl der Zeilen in der Abfrageausgabe.  
  
-   MIN(*Select_Item*)- Bestimmt den kleinsten Wert von *Select_Item* in einer Spalte.  
  
-   MAX(*Select_Item*)- Bestimmt den größten Wert von *Select_Item* in einer Spalte.  
  
-   SUM(*Select_Item*)-Totaliert eine Spalte mit numerischen Daten.  
  
 Sie können Feldfunktionen nicht verschachteln.  
  
 AS *Column_Name*  
 Gibt die Überschrift für eine Spalte in der Abfrageausgabe an. Dies ist nützlich, wenn *Select_Item* ein Ausdruck ist oder eine Feldfunktion enthält und Sie der Spalte einen aussagekräftigen Namen geben möchten. *Column_Name* kann ein Ausdruck sein, darf aber keine Zeichen (z. B. Leerzeichen) enthalten, die in Tabellenfeldnamen nicht zulässig sind.  
  
 VON [*Datenbankname*!] *Tabelle* [*Local_Alias*] [, [*Datenbankname*!] *Tabelle* [*Local_Alias*] ...]  
 Listet die Tabellen auf, die die von der Abfrage abgerufenen Daten enthalten. Wenn keine Tabelle geöffnet ist, zeigt Visual FoxPro das Dialogfeld **Öffnen** an, damit Sie den Speicherort der Datei angeben können. Nach dem Öffnen bleibt die Tabelle geöffnet, nachdem die Abfrage abgeschlossen ist.  
  
 *DatabaseName*! gibt den Namen einer anderen Datenbank als der mit der Datenquelle angegebenen an. Sie müssen den Namen der Datenbank einschließen, die die Tabelle enthält, wenn die Datenbank nicht mit der Datenquelle angegeben ist. Fügen Sie das Ausrufezeichen (!) nach dem Datenbanknamen und vor dem Tabellennamen ein.  
  
 *Local_Alias* gibt einen temporären Namen für die Tabelle mit dem Namen in *Tabelle*an. Wenn Sie einen lokalen Alias angeben, müssen Sie den lokalen Alias anstelle des Tabellennamens in der SELECT-Anweisung verwenden. Der lokale Alias wirkt sich nicht auf die Visual FoxPro-Umgebung aus.  
  
 WO *JoinCondition* [UND *JoinCondition* ...]    [UND &#124; ODER *FilterCondition* [und &#124; ODER *FilterCondition* ...]]  
 Weist Visual FoxPro an, nur bestimmte Datensätze in die Abfrageergebnisse aufzunehmen. WHERE ist erforderlich, um Daten aus mehreren Tabellen abzurufen.  
  
 *JoinCondition* gibt Felder an, die die Tabellen in der FROM-Klausel verknüpfen. Wenn Sie mehr als eine Tabelle in eine Abfrage einschließen, sollten Sie für jede Tabelle nach der ersten Tabelle eine Join-Bedingung angeben.  
  
> [!IMPORTANT]  
>  Berücksichtigen Sie beim Erstellen von Verknüpfungsbedingungen die folgenden Informationen:  
  
-   Wenn Sie zwei Tabellen in eine Abfrage einschließen und keine Join-Bedingung angeben, wird jeder Datensatz in der ersten Tabelle mit jedem Datensatz in der zweiten Tabelle verknüpft, solange die Filterbedingungen erfüllt sind. Eine solche Abfrage kann zu langen Ergebnissen führen.  
  
-   Seien Sie vorsichtig, wenn Sie Tabellen mit leeren Feldern verknüpfen, da Visual FoxPro leeren Feldern entspricht. Zum Beispiel, wenn Sie auf CUSTOMER beitreten. ZIP und INVOICE. ZIP und wenn CUSTOMER 100 leere Postleitzahlen und INVOICE 400 leere Postleitzahlen enthält, enthält die Abfrageausgabe 40.000 zusätzliche Datensätze, die sich aus den leeren Feldern ergeben. Verwenden Sie die Funktion **EMPTY( ),** um leere Datensätze aus der Abfrageausgabe zu entfernen.  
  
-   Sie müssen den AND-Operator verwenden, um mehrere Verknüpfungsbedingungen zu verbinden. Jede Join-Bedingung hat die folgende Form:  
  
     *FieldName1-Vergleich FieldName2*  
  
     *FieldName1* ist der Name eines Felds aus einer Tabelle, *FieldName2* der Name eines Felds aus einer anderen Tabelle, und *Vergleich* ist einer der in der folgenden Tabelle beschriebenen Operatoren.  
  
|Operator|Vergleich|  
|--------------|----------------|  
|=|Gleich|  
|==|Genau gleich|  
|LIKE|SQL LIKE|  
|<>, !=, #|Ungleich|  
|>|Mehr als|  
|>=|Mehr als oder gleich|  
|<|Kleiner als|  
|<=|Kleiner als oder gleich|  
  
 Wenn Sie den Operator = mit Zeichenfolgen verwenden, funktioniert er je nach Einstellung von SET ANSI unterschiedlich. Wenn SET ANSI auf OFF festgelegt ist, behandelt Visual FoxPro Zeichenfolgenvergleiche in einer Weise, die Xbase-Benutzern vertraut ist. Wenn SET ANSI auf ON festgelegt ist, folgt Visual FoxPro den ANSI-Standards für Zeichenfolgenvergleiche. Weitere Informationen dazu, wie Visual FoxPro Zeichenfolgenvergleiche durchführt, finden Sie unter [SET ANSI](../../odbc/microsoft/set-ansi-command.md) und [SET EXACT.](../../odbc/microsoft/set-exact-command.md)  
  
 *FilterCondition* gibt die Kriterien an, die Datensätze erfüllen müssen, um in die Abfrageergebnisse einbezogen zu werden. Sie können beweitete Filterbedingungen in eine Abfrage aufnehmen, wie Sie möchten, und sie mit dem OPERATOR AND oder OR verbinden. Sie können auch den Operator NOT verwenden, um den Wert eines logischen Ausdrucks umzukehren, oder Sie können **EMPTY(** verwenden, um nach einem leeren Feld zu suchen. *FilterCondition* kann eines der Formulare in den folgenden Beispielen annehmen:  
  
 **Beispiel 1** *FieldName1 Vergleich FieldName2*  
  
 `customer.cust_id = orders.cust_id`  
  
 **Beispiel 2** *FieldName-Vergleichsausdruck*  
  
 `payments.amount >= 1000`  
  
 **Beispiel 3** *FieldName Vergleich* ALL (*Unterquery*)  
  
 `company < ALL ;`  
  
 `(SELECT company FROM customer WHERE country = "USA")`  
  
 Wenn die Filterbedingung ALL enthält, muss das Feld die Vergleichsbedingung für alle Von der Unterabfrage generierten Werte erfüllen, bevor der Datensatz in die Abfrageergebnisse aufgenommen wird.  
  
 **Beispiel 4** *FieldName Vergleich* ANY &#124; SOME (*Unterquery*)  
  
 `company < ANY ;`  
  
 `(SELECT company FROM customer WHERE country = "USA")`  
  
 Wenn die Filterbedingung ANY oder SOME enthält, muss das Feld die Vergleichsbedingung für mindestens einen der von der Unterabfrage generierten Werte erfüllen.  
  
 Im folgenden Beispiel wird überprüft, ob die Werte im Feld innerhalb eines angegebenen Wertebereichs liegen:  
  
 **Beispiel 5** *FieldName* [NOT] ZWISCHEN *Start_Range* und *End_Range*  
  
 `customer.postalcode BETWEEN 90000 AND 99999`  
  
 Im folgenden Beispiel wird überprüft, ob mindestens eine Zeile die Kriterien in der Unterabfrage erfüllt. Wenn die Filterbedingung EXISTS enthält, wird die Filterbedingung als True (. T.) es sei denn, die Unterabfrage wird zum leeren Satz ausgewertet.  
  
 **Beispiel 6** [NOT] EXISTS (*Unterabfrage*)  
  
 `EXISTS ;`  
  
 `(SELECT * FROM orders WHERE customer.postalcode =`  
  
 `orders.postalcode)`  
  
 **Beispiel 7** *FieldName* [NOT] IN *Value_Set*  
  
 `customer.postalcode NOT IN ("98052","98072","98034")`  
  
 Wenn die Filterbedingung IN enthält, muss das Feld einen der Werte enthalten, bevor sein Datensatz in die Abfrageergebnisse aufgenommen wird.  
  
 **Beispiel 8** *FieldName* [NOT] IN (*Unterquery*)  
  
 `customer.cust_id IN ;`  
  
 `(SELECT orders.cust_id FROM orders WHERE orders.city="Seattle")`  
  
 Hier muss das Feld einen der von der Unterabfrage zurückgegebenen Werte enthalten, bevor der Datensatz in die Abfrageergebnisse aufgenommen wird.  
  
 **Beispiel 9** *FieldName* [NOT] LIKE *cExpression*  
  
 `customer.country NOT LIKE "USA"`  
  
 Diese Filterbedingung sucht nach jedem Feld, das mit *cExpression*übereinstimmt. Sie können das Prozentzeichen (%) verwenden. und unterstrichen ( _ ) Platzhalterzeichen als Teil von *cExpression*. Der Unterstrich stellt ein einzelnes unbekanntes Zeichen in der Zeichenfolge dar.  
  
 GRUPPE VON *GroupColumn* [, *GroupColumn* ...]  
 Gruppiert Zeilen in der Abfrage basierend auf Werten in einer oder mehreren Spalten. *GroupColumn* kann eine der folgenden sein:  
  
-   Der Name eines regulären Tabellenfelds.  
  
-   Ein Feld, das eine SQL-Feldfunktion enthält.  
  
-   Ein numerischer Ausdruck, der die Position der Spalte in der Ergebnistabelle angibt. (Die linke Spaltennummer ist 1.)  
  
 HAVING *FilterCondition*  
 Gibt eine Filterbedingung an, die Gruppen erfüllen müssen, um in die Abfrageergebnisse einbezogen zu werden. HAVING sollte mit GROUP BY verwendet werden und kann beweitet viele Filterbedingungen enthalten, die über den AND- oder ODER-Operator verbunden sind. Sie können auch NOT verwenden, um den Wert eines logischen Ausdrucks umzukehren.  
  
 *FilterCondition* kann keine Unterabfrage enthalten.  
  
 Eine HAVING-Klausel ohne GROUP BY-Klausel verhält sich wie eine WHERE-Klausel. Sie können lokale Aliase und Feldfunktionen in der HAVING-Klausel verwenden. Verwenden Sie eine WHERE-Klausel für eine schnellere Leistung, wenn Ihre HAVING-Klausel keine Feldfunktionen enthält.  
  
 [UNION [ALL] *SELECTCommand*]  
 Kombiniert die Endergebnisse eines SELECT mit den Endergebnissen eines anderen SELECT. Standardmäßig überprüft UNION die kombinierten Ergebnisse und eliminiert doppelte Zeilen. Verwenden Sie Klammern, um mehrere UNION-Klauseln zu kombinieren.  
  
 ALL verhindert, dass UNION doppelte Zeilen aus den kombinierten Ergebnissen eliminiert.  
  
 UNION-Klauseln folgen diesen Regeln:  
  
-   Sie können UNION nicht zum Kombinieren von Unterabfragen verwenden.  
  
-   Beide SELECT-Befehle müssen die gleiche Anzahl von Spalten in ihrer Abfrageausgabe aufweisen.  
  
-   Jede Spalte in den Abfrageergebnissen eines SELECT muss denselben Datentyp und dieselbe Breite aufweisen wie die entsprechende Spalte in der anderen SELECT.  
  
-   Nur die endgültige SELECT kann eine ORDER BY-Klausel haben, die auf Ausgabespalten nach Zahl verweisen muss. Wenn eine ORDER BY-Klausel enthalten ist, wirkt sie sich auf das vollständige Ergebnis aus.  
  
 Sie können auch die UNION-Klausel verwenden, um eine äußere Verknüpfung zu simulieren.  
  
 Wenn Sie zwei Tabellen in einer Abfrage verknüpfen, werden nur Datensätze mit übereinstimmenden Werten in den Verknüpfungsfeldern in die Ausgabe einbezogen. Wenn ein Datensatz in der übergeordneten Tabelle keinen entsprechenden Datensatz in der untergeordneten Tabelle enthält, ist der Datensatz in der übergeordneten Tabelle nicht in der Ausgabe enthalten. Mit einer äußeren Verknüpfung können Sie alle Datensätze in der übergeordneten Tabelle in die Ausgabe einschließen, zusammen mit den übereinstimmenden Datensätzen in der untergeordneten Tabelle. Um eine äußere Verknüpfung in Visual FoxPro zu erstellen, müssen Sie einen geschachtelten SELECT-Befehl verwenden, wie im folgenden Beispiel:  
  
```  
SELECT customer.company, orders.order_id, orders.emp_id ;  
FROM customer, orders ;  
WHERE customer.cust_id = orders.cust_id ;  
UNION ;  
SELECT customer.company, 0, 0 ;  
FROM customer ;  
WHERE customer.cust_id NOT IN ;  
(SELECT orders.cust_id FROM orders)  
```  
  
> [!NOTE]  
>  Stellen Sie sicher, dass Sie den Raum einschließen, der unmittelbar vor jedem Semikolon steht. Andernfalls wird eine Fehlermeldung angezeigt.  
  
 Der Abschnitt des Befehls vor der UNION-Klausel wählt Datensätze aus beiden Tabellen aus, die übereinstimmende Werte aufweisen. Die Debitorenunternehmen, denen keine zugeordneten Rechnungen zugeordnet sind, sind nicht enthalten. Der Abschnitt des Befehls nach der UNION-Klausel wählt Datensätze in der Debitorentabelle aus, die keine übereinstimmenden Datensätze in der Tabelle "Aufträge" enthalten.  
  
 Beachten Sie den zweiten Abschnitt des Befehls wie folgt:  
  
-   Die SELECT-Anweisung in den Klammern wird zuerst verarbeitet. Dieser Auszug erstellt eine Auswahl aller Debitorennummern in der Tabelle "Aufträge".  
  
-   Die WHERE-Klausel findet alle Debitorennummern in der Debitorentabelle, die nicht in der Tabelle "Bestellungen" enthalten sind. Da der erste Abschnitt des Befehls alle Unternehmen mit einer Kundennummer in der Tabelle "Bestellungen" bereitgestellt hat, werden nun alle Unternehmen in der Kundentabelle in die Abfrageergebnisse einbezogen.  
  
-   Da die Strukturen der Tabellen, die in einer UNION enthalten sind, identisch sein müssen, gibt es in der zweiten SELECT-Anweisung zwei Platzhalter, die *orders.order_id* und *orders.emp_id* aus der ersten SELECT-Anweisung darstellen.  
  
    > [!NOTE]  
    >  Die Platzhalter müssen denselben Typ wie die Felder aufweisen, die sie darstellen. Wenn es sich bei dem Feld um einen Datumstyp handelt, sollte der Platzhalter . Wenn es sich bei dem Feld um ein Zeichenfeld handelt, sollte der Platzhalter die leere Zeichenfolge ("" " sein" sein.  
  
 ORDER BY *Order_Item* [ASC &#124; DESC] [, *Order_Item* [ASC &#124; DESC] ...]  
 Sortiert die Abfrageergebnisse basierend auf den Daten in einer oder mehreren Spalten. Jede *Order_Item* muss einer Spalte in den Abfrageergebnissen entsprechen und kann eine der folgenden sein:  
  
-   Ein Feld in einer FROM-Tabelle, das auch ein ausgewähltes Element in der SELECT-Hauptklausel (nicht in einer Unterabfrage) ist.  
  
-   Ein numerischer Ausdruck, der die Position der Spalte in der Ergebnistabelle angibt. (Die linke Spalte ist die Nummer 1.)  
  
 ASC gibt eine aufsteigende Reihenfolge für Abfrageergebnisse entsprechend der Auftragsposition oder den Artikeln an und ist die Standardeinstellung für ORDER BY.  
  
 DESC gibt eine absteigende Reihenfolge für Abfrageergebnisse an.  
  
 Abfrageergebnisse werden ungeordnet angezeigt, wenn Sie keine Bestellung mit ORDER BY angeben.  
  
## <a name="remarks"></a>Bemerkungen  
 SELECT ist ein SQL-Befehl, der wie jeder andere Visual FoxPro-Befehl in Visual FoxPro integriert ist. Wenn Sie SELECT zum Stellen einer Abfrage verwenden, interpretiert Visual FoxPro die Abfrage und ruft die angegebenen Daten aus den Tabellen ab. Sie können eine SELECT-Abfrage entweder im Eingabeaufforderungsfenster oder in einem Visual FoxPro-Programm erstellen (wie bei jedem anderen Visual FoxPro-Befehl).  
  
> [!NOTE]  
>  SELECT beachtet nicht die aktuelle Filterbedingung, die mit SET FILTER angegeben wurde.  
  
## <a name="driver-remarks"></a>Driver-Bemerkungen  
 Wenn Ihre Anwendung die ODBC SQL-Anweisung SELECT an die Datenquelle sendet, konvertiert der Visual FoxPro ODBC-Treiber den Befehl ohne Übersetzung in den Befehl Visual FoxPro SELECT, es sei denn, der Befehl enthält eine ODBC-Escapesequenz. Elemente, die in einer ODBC-Escapesequenz eingeschlossen sind, werden in Visual FoxPro-Syntax konvertiert. Weitere Informationen zur Verwendung von ODBC-Escape-Sequenzen finden Sie unter [Zeit- und Datumsfunktionen](../../odbc/microsoft/time-and-date-functions-visual-foxpro-odbc-driver.md) und in der *Referenz des Microsoft ODBC-Programmierers*unter [Escape-Sequenzen in ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [TABELLE ERSTELLEN - SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [EINFÜGEN - SQL](../../odbc/microsoft/insert-sql-command.md)   
 [SET ANSI](../../odbc/microsoft/set-ansi-command.md)   
 [GENAU FESTLEGEN](../../odbc/microsoft/set-exact-command.md)
