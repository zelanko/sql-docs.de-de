---
description: SELECT (SQL-Befehl)
title: SELECT-SQL-Befehl | Microsoft-Dokumentation
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
ms.openlocfilehash: 2b5fb0e3d38a2e5594cacf77b116844bcce219d7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466422"
---
# <a name="select---sql-command"></a>SELECT (SQL-Befehl)
Ruft Daten aus einer oder mehreren Tabellen ab.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt die native Visual FoxPro-Sprachsyntax für diesen Befehl. Treiber spezifische Informationen finden Sie unter **Treiber Hinweise**.  
  
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
>  Eine *Unterabfrage*, auf die in den folgenden Argumenten verwiesen wird, ist eine SELECT-Abfrage innerhalb einer SELECT-Option und muss in Klammern eingeschlossen werden. Sie können in der WHERE-Klausel bis zu zwei Unterabfragen auf derselben Ebene (nicht in einem anderen) enthalten. (Weitere Informationen finden Sie im Abschnitt zu den Argumenten.) Unterabfragen können mehrere Joinbedingungen enthalten.  
  
 [Alle &#124; verschieden]   [*Alias*.] *Select_Item* [as *Column_Name*] [, [*Alias*.] *Select_Item* [as *Column_Name*]...]  
 Die SELECT-Klausel gibt die Felder, Konstanten und Ausdrücke an, die in den Abfrage Ergebnissen angezeigt werden.  
  
 Standardmäßig werden alle Zeilen in den Abfrage Ergebnissen angezeigt.  
  
 Unterschiedlich schließt Duplikate von Zeilen aus den Abfrage Ergebnissen aus.  
  
> [!NOTE]  
>  Sie können nur einmal pro SELECT-Klausel verwenden.  
  
 *Alias*. qualifiziert übereinstimmende Elementnamen. Jedes Element, das Sie mit *Select_Item* angeben, generiert eine Spalte der Abfrageergebnisse. Wenn mindestens zwei Elemente denselben Namen haben, schließen Sie den Tabellenalias und einen Punkt vor dem Elementnamen ein, um zu verhindern, dass Spalten dupliziert werden.  
  
 *Select_Item* gibt ein Element an, das in die Abfrageergebnisse eingeschlossen werden soll. Ein Element kann eines der folgenden sein:  
  
-   Der Name eines Felds aus einer Tabelle in der from-Klausel.  
  
-   Eine-Konstante, die angibt, dass der gleiche Konstante Wert in jeder Zeile der Abfrageergebnisse angezeigt werden soll.  
  
-   Ein Ausdruck, der den Namen einer benutzerdefinierten Funktion aufweisen kann.  
  
 **Benutzerdefinierte Funktionen mit SELECT**  
  
 Obwohl die Verwendung von benutzerdefinierten Funktionen in der SELECT-Klausel offensichtliche Vorteile bietet, sollten Sie auch die folgenden Einschränkungen beachten:  
  
-   Die Geschwindigkeit von Vorgängen, die mit SELECT ausgeführt werden, kann durch die Geschwindigkeit eingeschränkt werden, mit der solche benutzerdefinierten Funktionen ausgeführt werden. Manipulationen mit hohem Volumen, die benutzerdefinierte Funktionen betreffen, können besser durch die Verwendung von API und benutzerdefinierten Funktionen erzielt werden, die in C oder in der Assemblysprache geschrieben wurden.  
  
-   Die einzige zuverlässige Möglichkeit, Werte an benutzerdefinierte Funktionen zu übergeben, die von SELECT aufgerufen werden, ist die Argumentliste, die an die Funktion übergeben wird, wenn Sie aufgerufen wird.  
  
-   Selbst wenn Sie experimentieren und eine vermeintlich verbotene Bearbeitung entdecken, die in einer bestimmten Version von FoxPro ordnungsgemäß funktioniert, gibt es keine Garantie dafür, dass Sie in späteren Versionen weiterhin funktioniert.  
  
 Abgesehen von diesen Einschränkungen sind benutzerdefinierte Funktionen in der SELECT-Klausel zulässig. Beachten Sie jedoch, dass die Verwendung von SELECT die Leistung beeinträchtigen könnte.  
  
 Die folgenden Feld Funktionen sind für die Verwendung mit einem SELECT-Element verfügbar, bei dem es sich um ein Feld oder einen Ausdruck mit einem Feld handelt:  
  
-   AVG (*Select_Item*): Average a Average a Column of numeric Data.  
  
-   COUNT (*Select_Item*): zählt die Anzahl von SELECT-Elementen in einer Spalte. COUNT (*) zählt die Anzahl der Zeilen in der Abfrageausgabe.  
  
-   MIN (*Select_Item*): bestimmt den kleinsten Wert *Select_Item* in einer Spalte.  
  
-   Max (*Select_Item*): bestimmt den größten Wert *Select_Item* in einer Spalte.  
  
-   Sum (*Select_Item*): Gesamtergebnis einer Spalte mit numerischen Daten.  
  
 Feld Funktionen können nicht geschachtelt werden.  
  
 Wie *Column_Name*  
 Gibt die Überschrift für eine Spalte in der Abfrageausgabe an. Dies ist nützlich, wenn *Select_Item* ein Ausdruck ist oder eine Feldfunktion enthält und Sie der Spalte einen aussagekräftigen Namen einräumen möchten. *Column_Name* kann ein Ausdruck sein, aber keine Zeichen (z. b. Leerzeichen) enthalten, die in Tabellen Feldnamen nicht zulässig sind.  
  
 Aus [*DatabaseName*!] *Tabelle* [*Local_Alias*] [, [*DatabaseName*!] *Tabelle* [*Local_Alias*]...]  
 Listet die Tabellen auf, die die Daten enthalten, die von der Abfrage abgerufen werden. Wenn keine Tabelle geöffnet ist, zeigt Visual FoxPro das Dialogfeld **Öffnen** an, in dem Sie den Datei Speicherort angeben können. Nachdem Sie geöffnet wurde, bleibt die Tabelle geöffnet, nachdem die Abfrage abgeschlossen wurde.  
  
 *DatabaseName*! Gibt den Namen einer anderen Datenbank als der an, die mit der Datenquelle angegeben ist. Wenn die Datenbank nicht mit der Datenquelle angegeben ist, müssen Sie den Namen der Datenbank einschließen, in der die Tabelle enthalten ist. Schließen Sie das Ausrufezeichen (!) nach dem Datenbanknamen und vor dem Tabellennamen ein.  
  
 *Local_Alias* gibt einen temporären Namen für die in *Table*benannte Tabelle an. Wenn Sie einen lokalen Alias angeben, müssen Sie den lokalen Alias anstelle des Tabellennamens in der SELECT-Anweisung verwenden. Der lokale Alias hat keine Auswirkung auf die Visual FoxPro-Umgebung.  
  
 Wobei *joinCondition* [und *joinCondition* ...]    [Und &#124; oder *filtercondition* [und &#124; oder *filtercondition* ...]]  
 Weist Visual FoxPro an, nur bestimmte Datensätze in die Abfrageergebnisse einzubeziehen. Dabei ist erforderlich, um Daten aus mehreren Tabellen abzurufen.  
  
 *JoinCondition* gibt Felder an, die die Tabellen in der from-Klausel verknüpfen. Wenn Sie mehr als eine Tabelle in eine Abfrage einschließen, sollten Sie eine Joinbedingung für jede Tabelle nach dem ersten angeben.  
  
> [!IMPORTANT]  
>  Beachten Sie beim Erstellen von Joinbedingungen die folgenden Informationen:  
  
-   Wenn Sie zwei Tabellen in eine Abfrage einschließen und keine Joinbedingung angeben, wird jeder Datensatz in der ersten Tabelle mit jedem Datensatz in der zweiten Tabelle verknüpft, solange die Filterbedingungen erfüllt sind. Eine solche Abfrage kann lange Ergebnisse verursachen.  
  
-   Gehen Sie beim beitreten von Tabellen mit leeren Feldern vorsichtig vor, da Visual FoxPro leere Felder abgleicht. Wenn Sie z. b. an CUSTOMER.ZIP und INVOICE.ZIP teilnehmen und der Kunde 100 leere Postleitzahlen enthält und die Rechnung 400 leere Postleitzahlen enthält, enthält die Abfrageausgabe 40.000 zusätzliche Datensätze, die sich aus den leeren Feldern ergeben. Verwenden Sie die **empty ()** -Funktion, um leere Datensätze aus der Abfrageausgabe auszuschließen.  
  
-   Sie müssen den and-Operator verwenden, um mehrere Joinbedingungen zu verbinden. Jede Joinbedingung weist die folgende Form auf:  
  
     *FieldName1-Vergleich FieldName2*  
  
     *FieldName1* ist der Name eines Felds aus einer Tabelle, *FieldName2* ist der Name eines Felds aus einer anderen Tabelle, und der *Vergleich* ist einer der Operatoren, die in der folgenden Tabelle beschrieben werden.  
  
|Operator|Vergleich|  
|--------------|----------------|  
|=|Gleich|  
|==|Genau gleich|  
|LIKE|SQL like|  
|<>,! =, #|Ungleich|  
|>|Mehr als|  
|>=|Mehr als oder gleich|  
|<|Kleiner als|  
|<=|Kleiner als oder gleich|  
  
 Wenn Sie den =-Operator mit Zeichen folgen verwenden, verhält er sich abhängig von der Einstellung von SET ANSI anders. Wenn SET ANSI auf OFF festgelegt ist, behandelt Visual FoxPro Zeichen folgen Vergleiche auf eine Weise, die xbase-Benutzern vertraut. Wenn SET ANSI auf ON festgelegt ist, befolgt Visual FoxPro ANSI-Standards für Zeichen folgen Vergleiche. Weitere Informationen zur Durchführung von Zeichen folgen vergleichen durch Visual FoxPro finden Sie unter [SET ANSI](../../odbc/microsoft/set-ansi-command.md) und [Set Exact](../../odbc/microsoft/set-exact-command.md) .  
  
 *Filtercondition* gibt die Kriterien an, die Datensätze erfüllen müssen, damit Sie in die Abfrageergebnisse eingeschlossen werden. Sie können beliebig viele Filterbedingungen in eine Abfrage einschließen, indem Sie Sie mit dem and-Operator oder or-Operator verbinden. Sie können auch den Not-Operator verwenden, um den Wert eines logischen Ausdrucks umzukehren, oder Sie können **empty ()** verwenden, um nach einem leeren Feld zu suchen. *Filtercondition* kann in den folgenden Beispielen beliebige Formulare annehmen:  
  
 **Beispiel 1** *FieldName1 Vergleich FieldName2*  
  
 `customer.cust_id = orders.cust_id`  
  
 **Beispiel 2** *: FieldName-Vergleichs Ausdruck*  
  
 `payments.amount >= 1000`  
  
 **Beispiel 3** *FieldName Comparison* all (*Unterabfrage*)  
  
 `company < ALL ;`  
  
 `(SELECT company FROM customer WHERE country = "USA")`  
  
 Wenn die Filterbedingung all einschließt, muss das Feld die Vergleichs Bedingung für alle Werte erfüllen, die von der Unterabfrage generiert werden, bevor der Datensatz in den Abfrage Ergebnissen enthalten ist.  
  
 **Beispiel 4** *FieldName-Vergleich* Any &#124; some (*Unterabfrage*)  
  
 `company < ANY ;`  
  
 `(SELECT company FROM customer WHERE country = "USA")`  
  
 Wenn die Filterbedingung oder einige enthält, muss das Feld die Vergleichs Bedingung für mindestens einen der von der Unterabfrage generierten Werte erfüllen.  
  
 Im folgenden Beispiel wird überprüft, ob die Werte im-Feld innerhalb eines angegebenen Wertebereichs liegen:  
  
 **Beispiel 5** *Feldname* [nicht] zwischen *Start_Range* und *End_Range*  
  
 `customer.postalcode BETWEEN 90000 AND 99999`  
  
 Im folgenden Beispiel wird überprüft, ob mindestens eine Zeile die Kriterien in der Unterabfrage erfüllt. Wenn die Filterbedingung vorhanden ist, wird die Filterbedingung als true ausgewertet (. T.), es sei denn, die Unterabfrage ergibt den leeren Satz.  
  
 **Beispiel 6** [nicht] vorhanden (*Unterabfrage*)  
  
 `EXISTS ;`  
  
 `(SELECT * FROM orders WHERE customer.postalcode =`  
  
 `orders.postalcode)`  
  
 **Beispiel 7** *FieldName* [NOT] in *Value_Set*  
  
 `customer.postalcode NOT IN ("98052","98072","98034")`  
  
 Wenn die Filterbedingung in einschließt, muss das Feld einen der-Werte enthalten, bevor sein Datensatz in den Abfrage Ergebnissen enthalten ist.  
  
 **Beispiel 8** *FieldName* [NOT] in (*Unterabfrage*)  
  
 `customer.cust_id IN ;`  
  
 `(SELECT orders.cust_id FROM orders WHERE orders.city="Seattle")`  
  
 Hier muss das Feld einen der Werte enthalten, die von der Unterabfrage zurückgegeben werden, bevor der Datensatz in den Abfrage Ergebnissen enthalten ist.  
  
 **Beispiel 9** *FieldName* [nicht] wie *cexpression*  
  
 `customer.country NOT LIKE "USA"`  
  
 Diese Filterbedingung sucht nach jedem Feld, das *cexpression*entspricht. Sie können das Prozentzeichen (%) verwenden. und Unterstrich Zeichen (_) als Teil von *cexpression*. Der Unterstrich stellt ein einzelnes unbekanntes Zeichen in der Zeichenfolge dar.  
  
 Gruppieren nach *GroupColumn* [, *GroupColumn* ...]  
 Gruppiert Zeilen in der Abfrage auf der Grundlage von Werten in einer oder mehreren Spalten. *GroupColumn* kann eine der folgenden sein:  
  
-   Der Name eines regulären Tabellen Felds.  
  
-   Ein Feld, das eine SQL-Feldfunktion enthält.  
  
-   Ein numerischer Ausdruck, der den Speicherort der Spalte in der Ergebnistabelle angibt. (Die linke linke Spaltennummer ist 1.)  
  
 Mit *filtercondition*  
 Gibt eine Filterbedingung an, die Gruppen erfüllen müssen, um in die Abfrageergebnisse eingeschlossen zu werden. Muss mit Group by verwendet werden und kann beliebig viele Filterbedingungen enthalten, die mit dem and-Operator oder or-Operator verbunden sind. Sie können auch verwenden, um den Wert eines logischen Ausdrucks umzukehren.  
  
 " *Filtercondition* " kann keine Unterabfrage enthalten.  
  
 Eine WITH-Klausel ohne Group By-Klausel verhält sich wie eine WHERE-Klausel. Sie können lokale Aliase und Feld Funktionen in der-Klausel verwenden. Verwenden Sie eine WHERE-Klausel, um die Leistung zu beschleunigen, wenn die-Klausel keine Feld Funktionen enthält.  
  
 [Union [all] *SelectCommand*]  
 Kombiniert die endgültigen Ergebnisse einer SELECT-Option mit den Endergebnissen einer anderen SELECT-Option. In der Standardeinstellung werden die kombinierten Ergebnisse von Union überprüft und doppelte Zeilen vermieden. Verwenden Sie Klammern, um mehrere Union-Klauseln zu kombinieren.  
  
 All verhindert, dass Union doppelte Zeilen aus den kombinierten Ergebnissen entfernt.  
  
 Union-Klauseln befolgen die folgenden Regeln:  
  
-   Unterabfragen können nicht mithilfe von Union kombiniert werden.  
  
-   Beide SELECT-Befehle müssen in der Abfrageausgabe die gleiche Anzahl von Spalten aufweisen.  
  
-   Jede Spalte in den Abfrage Ergebnissen einer SELECT-Abfrage muss denselben Datentyp und dieselbe Breite aufweisen wie die entsprechende Spalte in der anderen SELECT-Spalte.  
  
-   Nur die endgültige SELECT-Klausel kann eine ORDER BY-Klausel aufweisen, die auf Ausgabespalten nach Zahl verweisen muss. Wenn eine ORDER BY-Klausel eingeschlossen wird, wirkt sich dies auf das gesamte Ergebnis aus.  
  
 Sie können auch die Union-Klausel verwenden, um einen äußeren Join zu simulieren.  
  
 Wenn Sie zwei Tabellen in einer Abfrage verknüpfen, sind nur Datensätze mit übereinstimmenden Werten in den Verknüpfungs Feldern in der Ausgabe enthalten. Wenn ein Datensatz in der übergeordneten Tabelle keinen entsprechenden Datensatz in der untergeordneten Tabelle enthält, ist der Datensatz in der übergeordneten Tabelle nicht in der Ausgabe enthalten. Mit einem äußeren Join können Sie alle Datensätze in der übergeordneten Tabelle in der Ausgabe zusammen mit den übereinstimmenden Datensätzen in der untergeordneten Tabelle einschließen. Zum Erstellen eines äußeren Joins in Visual FoxPro müssen Sie einen gruppierten SELECT-Befehl verwenden, wie im folgenden Beispiel gezeigt:  
  
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
>  Stellen Sie sicher, dass Sie den Speicherplatz einschließen, der jedem Semikolon unmittelbar vorangestellt ist. Andernfalls erhalten Sie eine Fehlermeldung.  
  
 Der-Abschnitt des-Befehls vor der Union-Klausel wählt Datensätze aus beiden Tabellen aus, die übereinstimmende Werte aufweisen. Die Kunden Unternehmen, denen keine Rechnungen zugeordnet sind, sind nicht enthalten. Der Abschnitt des Befehls nach der Union-Klausel wählt Datensätze in der Customer-Tabelle aus, die keine übereinstimmenden Datensätze in der Orders-Tabelle aufweisen.  
  
 Beachten Sie in Bezug auf den zweiten Abschnitt des Befehls Folgendes:  
  
-   Die SELECT-Anweisung innerhalb der Klammern wird zuerst verarbeitet. Diese Anweisung erstellt eine Auswahl aller Kunden zahlen in der Orders-Tabelle.  
  
-   Die WHERE-Klausel ermittelt alle Kundennummern in der Customer-Tabelle, die nicht in der Orders-Tabelle enthalten sind. Da im ersten Abschnitt des Befehls alle Unternehmen mit einer Kundennummer in der Tabelle Orders bereitgestellt wurden, sind alle Unternehmen in der Customer-Tabelle nun in den Abfrage Ergebnissen enthalten.  
  
-   Da die Strukturen von Tabellen, die in einer Union enthalten sind, identisch sein müssen, gibt es in der zweiten SELECT-Anweisung zwei Platzhalter, um *Orders. order_id* und *Orders. emp_id* in der ersten SELECT-Anweisung darzustellen.  
  
    > [!NOTE]  
    >  Die Platzhalter müssen denselben Typ aufweisen wie die Felder, die Sie darstellen. Wenn es sich bei dem Feld um einen Datentyp handelt, sollte der Platzhalter {//} lauten. Wenn das Feld ein Zeichenfeld ist, muss der Platzhalter eine leere Zeichenfolge ("") sein.  
  
 Order by *Order_Item* [ASC &#124; Besc] [, *Order_Item* [ASC &#124; de]...]  
 Sortiert die Abfrageergebnisse auf der Grundlage der Daten in einer oder mehreren Spalten. Jede *Order_Item* muss einer Spalte in den Abfrage Ergebnissen entsprechen und kann eine der folgenden sein:  
  
-   Ein Feld in einer FROM-Tabelle, das auch ein SELECT-Element in der Main SELECT-Klausel ist (nicht in einer Unterabfrage).  
  
-   Ein numerischer Ausdruck, der den Speicherort der Spalte in der Ergebnistabelle angibt. (Die Spalte ganz links ist Nummer 1.)  
  
 ASC gibt eine aufsteigende Reihenfolge für Abfrageergebnisse entsprechend der Bestell Elemente an und ist die Standardeinstellung für Order by.  
  
 Der absteigend gibt eine absteigende Reihenfolge für Abfrageergebnisse an.  
  
 Die Abfrageergebnisse werden ungeordnet angezeigt, wenn Sie keine Bestellung mit Order by angeben.  
  
## <a name="remarks"></a>Bemerkungen  
 SELECT ist ein SQL-Befehl, der wie ein beliebiger anderer Visual FoxPro-Befehl in Visual FoxPro integriert ist. Wenn Sie SELECT zum Darstellen einer Abfrage verwenden, wird die Abfrage von Visual FoxPro interpretiert, und die angegebenen Daten werden aus den Tabellen abgerufen. Sie können eine SELECT-Abfrage entweder im Eingabe Aufforderungs Fenster oder in einem Visual FoxPro-Programm erstellen (wie bei jedem anderen Visual FoxPro-Befehl).  
  
> [!NOTE]  
>  Select verwendet nicht die aktuelle Filterbedingung, die mit Set Filter angegeben wird.  
  
## <a name="driver-remarks"></a>Hinweise zu Treibern  
 Wenn die Anwendung die ODBC-SQL-Anweisung SELECT an die Datenquelle sendet, konvertiert der Visual FoxPro-ODBC-Treiber den Befehl ohne Übersetzung in den Befehl Visual FoxPro SELECT, es sei denn, der Befehl enthält eine ODBC-Escapesequenz. In eine ODBC-Escapesequenz eingeschlossene Elemente werden in die Syntax von Visual FoxPro konvertiert. Weitere Informationen zur Verwendung von ODBC-Escapesequenzen finden Sie unter [Zeit-und Datumsfunktionen](../../odbc/microsoft/time-and-date-functions-visual-foxpro-odbc-driver.md) und in der *Microsoft ODBC Programmer es Reference (Escapesequenzen* [in ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md)).  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE TABLE-SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT-SQL](../../odbc/microsoft/insert-sql-command.md)   
 [ANSI festlegen](../../odbc/microsoft/set-ansi-command.md)   
 [exakte festlegen](../../odbc/microsoft/set-exact-command.md)
