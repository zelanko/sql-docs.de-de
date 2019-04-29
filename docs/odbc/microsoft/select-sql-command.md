---
title: SELECT – SQL-Befehl | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0c2d991afa179fdfbb536853e302b33de8bf12e1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63127874"
---
# <a name="select---sql-command"></a>SELECT (SQL-Befehl)
Ruft Daten aus einer oder mehreren Tabellen ab.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt die systemeigene Visual FoxPro-Sprachsyntax für diesen Befehl. Treiberspezifische Informationen finden Sie **Treiber "Hinweise"**.  
  
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
>  Ein *Unterabfrage*, in der folgenden Argumente bezeichnet werden, wird eine SELECT-Anweisung in einer SELECT-Anweisung und muss in Klammern eingeschlossen werden. Sie können bis zu zwei Unterabfragen haben, klicken Sie auf der gleichen Ebene (nicht geschachtelt) in der WHERE-Klausel. (Siehe diesen Abschnitt der Argumente.) Unterabfragen können mehrere Join-Bedingungen enthalten.  
  
 [Alle &#124; DISTINCT]   [*Alias*.] *Select_Item* [AS *Column_Name*] [, [*Alias*.] *Select_Item* [AS *Column_Name*]...]  
 Die SELECT-Klausel gibt an, die Felder, Konstanten und Ausdrücke, die in den Abfrageergebnissen angezeigt werden.  
  
 In der Standardeinstellung alle zeigt alle Zeilen in den Abfrageergebnissen.  
  
 DISTINCT werden Duplikate von Zeilen aus den Abfrageergebnissen ausgeschlossen.  
  
> [!NOTE]  
>  Sie können die DISTINCT nur einmal pro SELECT-Klausel verwenden.  
  
 *Alias*. qualifiziert die entsprechenden Elementnamen. Jedes Element, das Sie angeben, mit *Select_Item* generiert eine Spalte der Ergebnisse der Abfrage. Wenn zwei oder mehr Elemente den gleichen Namen haben, enthalten Sie den Tabellenalias und einen Punkt vor der Elementname, die verhindern, dass Spalten dupliziert wird.  
  
 *Select_Item* gibt ein Element in die Ergebnisse der Abfrage eingeschlossen werden. Ein Element kann einen der folgenden sein:  
  
-   Der Name eines Felds aus einer Tabelle in der FROM-Klausel.  
  
-   Eine Konstante gibt an, dass denselben Konstante Wert wird in jeder Zeile der Abfrageergebnisse angezeigt werden.  
  
-   Ein Ausdruck, der den Namen einer benutzerdefinierten Funktion sein kann.  
  
 **Benutzerdefinierte Funktionen mit SELECT-Anweisung**  
  
 Obwohl durch die Verwendung von benutzerdefinierten Funktionen in der SELECT-Klausel hat offensichtliche Vorteile, berücksichtigen Sie auch die folgenden Einschränkungen:  
  
-   Die Geschwindigkeit von Operationen, die mit SELECT-Anweisung kann die Geschwindigkeit beschränkt sein, an dem diese benutzerdefinierte Funktionen ausgeführt werden. Umfangreiche Bearbeitungen, die im Zusammenhang mit benutzerdefinierten Funktionen möglicherweise besser erfüllt werden, mithilfe von API- und benutzerdefinierte Funktionen, die in C oder Assemblysprache geschrieben.  
  
-   Die einzig zuverlässige Möglichkeit zum Übergeben von Werten für benutzerdefinierte Funktionen, die über Option aufgerufen wird, von der Argumentliste, die an die Funktion übergeben wird, wenn sie aufgerufen wird.  
  
-   Selbst wenn Sie experimentieren und ermitteln eine angeblich unzulässige Änderung, die in einer bestimmten Version von FoxPro ordnungsgemäß funktioniert, besteht keine Garantie dafür, die sie in späteren Versionen funktionieren weiterhin.  
  
 Abgesehen von diesen Einschränkungen sind benutzerdefinierte Funktionen in der SELECT-Klausel zulässig. Beachten Sie jedoch, dass es sich bei Verwenden von SELECT, die Leistung beeinträchtigen kann.  
  
 Die folgenden Funktionen sind verfügbar für die Verwendung mit einer select-Element, das ein Feld oder ein Ausdruck, der ein Feld ist:  
  
-   AVG (*Select_Item*) – eine Spalte mit numerischen Daten ermittelt.  
  
-   COUNT (*Select_Item*)-zählt die Anzahl der Elemente in einer Spalte auswählen. Count(*) zählt die Anzahl der Zeilen in der Ausgabe der Abfrage.  
  
-   MIN (*Select_Item*)-ermittelt den kleinsten Wert der *Select_Item* in einer Spalte.  
  
-   MAX (*Select_Item*)-ermittelt den größten Wert der *Select_Item* in einer Spalte.  
  
-   SUM (*Select_Item*)-Zeilengesamtwerte eine Spalte mit numerischen Daten.  
  
 Sie können keine Funktionen schachteln.  
  
 AS *Column_Name*  
 Gibt die Spaltenüberschrift, um eine Spalte in der Ausgabe der Abfrage an. Dies ist nützlich, wenn *Select_Item* ist ein Ausdruck oder enthält ein Feld-Funktion und der Spalte einen aussagekräftigen Namen geben möchten. *Column_name* kann ein Ausdruck sein, aber können keine Zeichen enthalten (z. B. Leerzeichen), die in Tabelle Feldnamen nicht zulässig sind.  
  
 AUS [*DatabaseName*!] *Tabelle* [*Local_Alias*] [, [*DatabaseName*!] *Tabelle* [*Local_Alias*]...]  
 Listet die Tabellen, die Daten enthalten, die die Abfrage abgerufen. Wenn keine Tabelle geöffnet ist, zeigt Visual FoxPro der **öffnen** Dialogfeld, sodass Sie den Dateispeicherort angeben können. Nachdem er geöffnet wurde, bleibt in der Tabelle geöffnet, nachdem die Abfrage abgeschlossen ist.  
  
 *DatabaseName*! Gibt den Namen einer Datenbank nicht mit der Datenquelle angegeben. Sie müssen den Namen der Datenbank enthalten, die in der Tabelle enthält, wenn die Datenbank mit der Datenquelle nicht angegeben ist. Schließen Sie das Ausrufezeichen (!)-Trennzeichen an, nach dem Datenbanknamen und vor dem Tabellennamen.  
  
 *Local_Alias* gibt an, für die Tabelle mit dem Namen in einen temporären Namen *Tabelle*. Wenn Sie einen lokalen Alias angeben, müssen Sie den lokalen Alias statt des Tabellennamens in der SELECT-Anweisung verwenden. Der lokale Alias wirkt sich nicht auf die Visual FoxPro-Umgebung aus.  
  
 WO *JoinCondition* [AND *JoinCondition* ...]    [AND &#124; oder *FilterCondition* [AND &#124; oder *FilterCondition* ...]]  
 Teilt Visual FoxPro, nur bestimmte Datensätze in den Abfrageergebnissen enthalten. Wenn zum Abrufen von Daten aus mehreren Tabellen erforderlich ist.  
  
 *JoinCondition* werden Felder, die die Tabellen in der FROM-Klausel zu verknüpfen. Wenn Sie mehr als eine Tabelle in einer Abfrage einschließen, sollten Sie eine Join-Bedingung für jede Tabelle nach dem ersten angeben.  
  
> [!IMPORTANT]  
>  Beachten Sie die folgenden Informationen an, bei der Erstellung von Join-Bedingungen:  
  
-   Wenn Sie zwei Tabellen in einer Abfrage enthalten, und Sie eine Join-Bedingung nicht geben, wird jeder Datensatz in der ersten Tabelle auf jeder Datensatz in der zweiten Tabelle verknüpft, solange der filterbedingungen erfüllt sind. Eine solche Abfrage kann es sich um längere Ergebnislisten zu erzeugen.  
  
-   Verwenden Sie vorsichtig beim Verknüpfen von Tabellen mit leeren Feldern, da Visual FoxPro leere Felder entspricht. Beispielsweise, wenn Sie Kunden verknüpfen. ZIP-Datei und Rechnung. KOMPRIMIEREN, und wenn Kunden 100 leere Postleitzahlen enthält und Rechnung 400 leere Postleitzahlen, enthält die Ausgabe der Abfrage 40.000 zusätzliche Datensätze, die durch die leeren Felder. Verwenden der **(leer)** Funktion, um leere Datensätze aus der Ausgabe der Abfrage zu entfernen.  
  
-   Sie müssen den AND-Operator verwenden, die Verbindung mehrere Join-Bedingungen. Jede Join-Bedingung hat folgendes Format:  
  
     *FieldName1 Vergleich FieldName2*  
  
     *FieldName1* ist der Name eines Felds aus einer Tabelle, *FieldName2* ist der Name eines Felds aus einer anderen Tabelle, und *Vergleich* ist einer der Operatoren in der folgenden Tabelle beschrieben.  
  
|Operator|Vergleich|  
|--------------|----------------|  
|=|Gleich|  
|==|Genau gleich.|  
|LIKE|SQL LIKE|  
|<>, !=, #|Ungleich|  
|>|Mehr als|  
|>=|Größer als oder gleich|  
|<|Kleiner als|  
|<=|Kleiner als oder gleich|  
  
 Bei Verwendung der =-Operator mit Zeichenfolgen, fungiert unterschiedlich, abhängig von der Einstellung von SET ANSI. Wenn SET ANSI auf OFF festgelegt ist, behandelt der Visual FoxPro Zeichenfolgenvergleiche Weise eine Xbase-Benutzern vertraut sind. Wenn SET ANSI auf ON festgelegt ist, folgt Visual FoxPro ANSI-Standards für Zeichenfolgenvergleiche an. Finden Sie unter [SET ANSI](../../odbc/microsoft/set-ansi-command.md) und [SET EXACT](../../odbc/microsoft/set-exact-command.md) für Weitere Informationen darüber, wie der Visual FoxPro Zeichenfolgenvergleiche durchführt.  
  
 *FilterCondition* gibt die Kriterien, die Datensätze erfüllen müssen, um in den Abfrageergebnissen enthalten sein. Sie können wie viele Bedingungen in einer Abfrage filtern, wie bei AND werden sollen, einschließen oder OR-Operator. Sie können auch den NOT-Operator verwenden, um den Wert eines logischen Ausdrucks umzukehren, Sie können auch **(leer)** zu prüfen, ein leeres Feld. *FilterCondition* dauert die Formulare in den folgenden Beispielen:  
  
 **Beispiel 1** *FieldName1 Vergleich FieldName2*  
  
 `customer.cust_id = orders.cust_id`  
  
 **Beispiel 2** *FieldName Vergleichsausdruck*  
  
 `payments.amount >= 1000`  
  
 **Beispiel 3** *FieldName Vergleich* alle (*Unterabfrage*)  
  
 `company < ALL ;`  
  
 `(SELECT company FROM customer WHERE country = "USA")`  
  
 Wenn die filterbedingung alle enthält, muss das Feld erfüllen, die vergleichsbedingung für alle Werte, die von der Unterabfrage generiert werden, bevor ein Datensatz in die Ergebnisse der Abfrage enthalten ist.  
  
 **Beispiel 4** *FieldName Vergleich* ANY &#124; SOME (*Unterabfrage*)  
  
 `company < ANY ;`  
  
 `(SELECT company FROM customer WHERE country = "USA")`  
  
 Wenn die filterbedingung alle oder einige enthält, muss das Feld der vergleichsbedingung für wenigstens einen der Werte von der Unterabfrage generiert erfüllen.  
  
 Im folgenden Beispiel wird überprüft, ob die Werte in das Feld in einem angegebenen Bereich von Werten sind:  
  
 **Beispiel 5** *FieldName* [NOT] zwischen *Start_Range* und *End_Range*  
  
 `customer.postalcode BETWEEN 90000 AND 99999`  
  
 Im folgenden Beispiel wird überprüft, ob mindestens eine Zeile mit die Kriterien in der Unterabfrage entspricht. Wenn die filterbedingung EXISTS enthält, die filterbedingung ergibt "true" (. T.), wenn die Unterabfrage beispielsweise die leerer Satz ausgewertet wird.  
  
 **Beispiel 6** [NOT] EXISTS (*Unterabfrage*)  
  
 `EXISTS ;`  
  
 `(SELECT * FROM orders WHERE customer.postalcode =`  
  
 `orders.postalcode)`  
  
 **Beispiel 7** *FieldName* [NOT] IN *Value_Set*  
  
 `customer.postalcode NOT IN ("98052","98072","98034")`  
  
 Wenn die filterbedingung IN enthält, muss das Feld enthalten die Werte vor der Datensatz in die Ergebnisse der Abfrage enthalten ist.  
  
 **Beispiel 8** *FieldName* [NOT] IN (*Unterabfrage*)  
  
 `customer.cust_id IN ;`  
  
 `(SELECT orders.cust_id FROM orders WHERE orders.city="Seattle")`  
  
 Hier muss das Feld enthalten die Werte, die von der Unterabfrage zurückgegeben wird, bevor Sie ein Datensatz in die Ergebnisse der Abfrage enthalten ist.  
  
 **Beispiel 9** *FieldName* [NOT] LIKE *cExpression*  
  
 `customer.country NOT LIKE "USA"`  
  
 Die filterbedingung für jedes Feld, das entspricht sucht *cExpression*. Sie können die Prozentzeichen (%) verwenden. und Platzhalterzeichen Unterstrich (_), als Teil des *cExpression*. Der Unterstrich stellt ein unbekanntes einzelnes Zeichen in der Zeichenfolge dar.  
  
 GROUP BY *GroupColumn* [, *GroupColumn* ...]  
 Gruppiert die Zeilen in der Abfrage basierend auf Werten in einer oder mehreren Spalten. *GroupColumn* kann einen der folgenden sein:  
  
-   Der Name eines Felds normale Tabelle.  
  
-   Ein Feld, das eine SQL-Feld-Funktion enthält.  
  
-   Ein numerischer Ausdruck, der die Position der Spalte in der Ergebnistabelle angibt. (Die Nummer der am weitesten links stehende Spalte ist 1.)  
  
 MIT *FilterCondition*  
 Gibt eine filterbedingung, die Gruppen erfüllen müssen, um in den Abfrageergebnissen enthalten sein. HAVING mit GROUP BY verwendet werden sollte und zählen, wie viele Bedingungen filtern, wie durch das AND verbunden werden sollen, oder OR-Operator. Sie können auch nicht den Wert eines logischen Ausdrucks umzukehren.  
  
 *FilterCondition* darf keine Unterabfrage enthalten.  
  
 Eine HAVING-Klausel ohne GROUP BY-Klausel verhält sich wie eine WHERE-Klausel. Sie können lokale Aliase und Funktionen in der HAVING-Klausel verwenden. Verwenden Sie eine WHERE-Klausel für eine bessere Leistung, wenn die HAVING-Klausel keine Funktionen enthält.  
  
 [[ALL] UNION *SELECTCommand*]  
 Kombiniert die Endergebnisse zu der eine SELECT-Anweisung mit die Endergebnisse zu der eine andere SELECT-Anweisung. In der Standardeinstellung UNION die kombinierten Ergebnissen überprüft und entfernt mehrfach auftretende Zeilen. Verwenden Sie Klammern, um mehrere UNION-Klauseln zu kombinieren.  
  
 Alle wird verhindert, dass UNION Eliminieren von doppelten Zeilen aus den kombinierten Ergebnissen.  
  
 UNION-Klausel gelten folgende Regeln:  
  
-   UNION können keine um Unterabfragen zu kombinieren.  
  
-   Beide SELECT-Befehle müssen die gleiche Anzahl von Spalten in die Abfrageausgabe.  
  
-   Jede Spalte in den Abfrageergebnissen, der eine SELECT-Anweisung müssen den gleichen Datentyp und die Breite der entsprechenden Spalte in die andere SELECT-Anweisung.  
  
-   Nur die letzte SELECT-Anweisung kann eine ORDER BY-Klausel haben Ausgabespalten Anzahl verweisen muss. Wenn eine ORDER BY-Klausel enthalten ist, wird das vollständige Ergebnis beeinträchtigt.  
  
 Sie können auch die UNION-Klausel verwenden, ein äußeren Joins zu simulieren.  
  
 Wenn Sie zwei Tabellen in einer Abfrage verbinden, sind nur Datensätze mit übereinstimmenden Werten in den verknüpften Feldern in der Ausgabe enthalten. Wenn ein Datensatz in der übergeordneten Tabelle nicht über einen entsprechenden Datensatz in der untergeordneten Tabelle verfügt, ist der Datensatz in der übergeordneten Tabelle in der Ausgabe nicht enthalten. Ein äußerer Join können Sie alle Datensätze in der übergeordneten Tabelle in der Ausgabe zusammen mit der übereinstimmenden Datensätze in der untergeordneten Tabelle einschließen. Um einen äußeren Join in der Visual FoxPro erstellen zu können, müssen Sie einen geschachtelte SELECT-Befehl aus, wie im folgenden Beispiel verwenden:  
  
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
>  Stellen Sie sicher, dass Sie den Speicherplatz einschließen, der jedem Semikolon unmittelbar vorangestellt. Andernfalls erhalten Sie einen Fehler.  
  
 Im Abschnitt des Befehls, bevor die UNION-Klausel Datensätze aus beiden Tabellen ausgewählt haben, übereinstimmenden Werten. Die von Kundenunternehmen, die keine zugeordneten Rechnungen sind nicht enthalten. Der Abschnitt des Befehls nach der UNION-Klausel wählt die Datensätze in der Customer-Tabelle, die keine übereinstimmenden Datensätze in der Orders-Tabelle.  
  
 In Bezug auf den zweiten Abschnitt des Befehls Beachten Sie Folgendes ein:  
  
-   Die SELECT-Anweisung innerhalb der Klammern wird zuerst verarbeitet. Diese Anweisung erstellt eine Auswahl von Zahlen für alle Kunden in der Orders-Tabelle.  
  
-   Die WHERE-Klausel sucht alle Kundennummern in der Customer-Tabelle, die nicht in der Orders-Tabelle enthalten sind. Da der erste Abschnitt des Befehls alle Unternehmen zur Verfügung, die eine Kundennummer in der Orders-Tabelle verfügen gestellt, sind alle Unternehmen in der Customer-Tabelle jetzt in den Abfrageergebnissen enthalten.  
  
-   Da die Strukturen in einer UNION enthaltenen Tabellen identisch sein müssen, müssen Sie zwei Platzhalter vorhanden sind, in die zweite SELECT-Anweisung zur Darstellung *Customer* und *orders.emp_id* wählen Sie in der ersten -Anweisung.  
  
    > [!NOTE]  
    >  Der Platzhalter muss denselben Typ wie die Felder, die sie darstellen. Wenn das Feld ein Date-Datentyp ist, muss der Platzhalter {/ /}. Wenn das Feld ein Zeichenfeld, sollte der Platzhalter die leere Zeichenfolge ("").  
  
 SORTIERT nach dem *Order_Item* [ASC &#124; DESC] [, *Order_Item* [ASC &#124; DESC]...]  
 Sortiert die Ergebnisse der Abfrage anhand der Daten in einer oder mehreren Spalten an. Jede *Order_Item* muss auf eine Spalte in die Ergebnisse der Abfrage entsprechen, und kann einen der folgenden sein:  
  
-   Ein Feld in einer FROM-Tabelle, die auch eine select-Element in der main-SELECT-Klausel (nicht in einer Unterabfrage) ist.  
  
-   Ein numerischer Ausdruck, der die Position der Spalte in der Ergebnistabelle angibt. (Entspricht der Anzahl die am weitesten links stehende Spalte 1.)  
  
 ASC gibt eine aufsteigende Reihenfolge für Abfrageergebnisse, gemäß der Reihenfolge-Elements oder der Elemente, und ist die Standardeinstellung für ORDER BY.  
  
 DESC gibt eine absteigende Reihenfolge für Abfrageergebnisse an.  
  
 Abfrageergebnisse werden nicht sortiert angezeigt, wenn Sie eine Bestellung nicht mit ORDER BY angeben.  
  
## <a name="remarks"></a>Hinweise  
 Wählen Sie ist ein SQL‑Befehl, der in der Visual FoxPro wie jeder andere Visual FoxPro-Befehl erstellt wird. Bei Verwendung von auswählen, um eine Abfrage darstellen, Visual FoxPro, interpretiert die Abfrage, und ruft die angegebenen Daten aus den Tabellen ab. Sie können eine SELECT-Abfrage entweder im Eingabeaufforderungsfenster oder in einer Visual FoxPro-Anwendung (wie bei jeder andere Visual FoxPro-Befehl) erstellen.  
  
> [!NOTE]  
>  Wählen Sie berücksichtigt nicht die aktuellen filterbedingung angegeben werden, mit dem FILTER festlegen.  
  
## <a name="driver-remarks"></a>Treiber "Hinweise".  
 Wenn Ihre Anwendung die ODBC-SQL-Anweisung SELECT an die Datenquelle sendet, konvertiert der Visual FoxPro-ODBC-Treiber, wenn der Befehl eine ODBC-Escapesequenz enthält den Befehl in der Visual FoxPro-wählen-Befehl ohne Übersetzung an. In einer ODBC-Escapesequenz Klammern angegebenen Elemente werden in Visual FoxPro-Syntax konvertiert. Weitere Informationen zur Verwendung von ODBC-Escapesequenzen, finden Sie unter [Zeit- und Datumsfunktionen](../../odbc/microsoft/time-and-date-functions-visual-foxpro-odbc-driver.md) und klicken Sie in der *Microsoft ODBC Programmer's Reference*, finden Sie unter [Escapesequenzen in ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md) .  
  
## <a name="see-also"></a>Siehe auch  
 [ERSTELLEN DER TABELLE - SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT - SQL](../../odbc/microsoft/insert-sql-command.md)   
 [SET ANSI](../../odbc/microsoft/set-ansi-command.md)   
 [LEGEN SIE GENAUE](../../odbc/microsoft/set-exact-command.md)
