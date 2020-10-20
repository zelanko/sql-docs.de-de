---
description: Projekteinstellungen (Konvertierung) (SybaseToSQL)
title: Projekteinstellungen (Konvertierung) (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/19/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: eeb80fa5-f530-4f21-beee-25f5a4b8ace6
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 1f4d616b964a1e9e9eed391e3386b16e9df54e44
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92195532"
---
# <a name="project-settings-conversion-sybasetosql"></a>Projekteinstellungen (Konvertierung) (SybaseToSQL)

Die Seite **Konvertierung** des Dialog Felds **Projekteinstellungen** enthält Einstellungen, die anpassen, wie SSMA die Syntax von SAP Adaptive Server Enterprise (ASE) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Syntax konvertiert.

Der Bereich **Konvertierung** ist in den Dialogfeldern **Projekteinstellungen** und **Standard Projekteinstellungen** verfügbar:

- Wenn Sie Einstellungen für alle SSMA-Projekte angeben möchten, wählen Sie **im Menü Extras** die **Option Standard Projekteinstellungen**aus, klicken Sie unten im linken Bereich auf **Allgemein** , und klicken Sie dann auf **Konvertierung**.

- Um Einstellungen für das aktuelle Projekt anzugeben, wählen Sie **im Menü Extras** die **Option Projekteinstellungen**aus, klicken Sie unten im linken Bereich auf **Allgemein** , und klicken Sie dann auf **Konvertierung**.

## <a name="miscellaneous-section"></a>Sonstige (Abschnitt)

### <a name="error"></a>@@ERROR

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Azure SQL und ASE verwenden andere Fehlercodes.

Verwenden Sie diese Einstellung, um den Typ der Meldung (Warnung oder Fehler) anzugeben, die SSMA im Ausgabe-oder Fehlerliste Bereich anzeigt, wenn im ASE-Code auf einen Verweis auf zugegriffen wird `@@ERROR` .

- Wenn Sie **konvertieren und mit Warnung markieren**auswählen, werden die Anweisungen von SSMA konvertiert und mit Warn Kommentaren markiert.
- Wenn Sie **mit Fehler markieren**auswählen, wird die Konvertierung von SSMA übersprungen und die Anweisungen mit den Fehler Kommentaren markiert.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Konvertieren und Markierung mit Warnung|
|Optimistisch|Konvertieren und Markierung mit Warnung|
|Vollständig|Mit Fehler markieren|

### <a name="conversion-of-like-operator"></a>Konvertierung des LIKE-Operators

Gibt an, ob die `LIKE` Operanden in das SAP ASE-Verhalten konvertiert werden sollen. Der Punkt ist, dass die ASE nachfolgende Leerzeichen in einem like-Muster schneidet. Die Problem Umgehung besteht darin, eine Umwandlung eines Right-Ausdrucks in einen Datentyp mit fester Länge mit einer maximalen Genauigkeit vorzunehmen.
  
- Wählen Sie **einfache Konvertierung** aus, um die Ausdrücke ohne Korrektur zu konvertieren.
- Um das ASE-Verhalten zu verwenden, wählen Sie Umwandlung **in eine Fixed-Länge**
  
Wenn Sie im Feld Modus einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Einfache Konvertierung|
|Optimistisch|Einfache Konvertierung|
|Vollständig|In eine Länge mit fester Länge umwandeln|

### <a name="convert-or-cast-empty-strings-to-numeric-types"></a>Konvertieren oder umwandeln leerer Zeichen folgen in numerische Typen

Gibt an, wie leere oder leere Zeichen folgen innerhalb von- `CONVERT` oder- `CAST` Ausdrücken mit einem numerischen Typ als Datentyp-Argument behandelt werden. Die folgenden Optionen sind für diese Einstellung verfügbar:

- Wählen Sie **einfache Konvertierung** aus, um die Ausdrücke ohne Korrektur zu konvertieren.
- Wenn eine **leere Zeichenfolge als numerischer Wert 0** ausgewählt ist, wird der Zeichen folgen Parameter durch `{s}` `CASE ltrim(rtrim({s})) WHEN "" THEN 0 else {s} END` Expression ersetzt.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Einfache Konvertierung|
|Optimistisch|Einfache Konvertierung|
|Vollständig|Leere Zeichenfolge als 0 (null)|

### <a name="concatenation-of-null"></a>Verkettung von NULL

Diese Einstellung gibt an, wie Zeichen folgen Verkettung mit konvertiert werden `NULL` . Die folgenden Optionen können für diese spezielle Einstellung festgelegt werden:

- Wenn die Option **Wrap with ISNULL function** ausgewählt ist, wird jede nicht Konstante `string_expression` in Verkettung mit umschlossen, `ISNULL(string_expression)` und `NULL` e wird durch eine leere Zeichenfolge ersetzt.
- Bei Beibehaltung der **aktuellen Syntax** wird die ursprüngliche Syntax beibehalten.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Aktuelle Syntax beibehalten|
|Optimistisch|Aktuelle Syntax beibehalten|
|Vollständig|Wrap mit IsNull-Funktion|

### <a name="conversion-of-empty-strings"></a>Konvertierung von leeren Zeichen folgen

Diese Einstellung gibt an, wie leere Zeichen folgen konvertiert werden. Die folgenden Optionen können für diese spezielle Einstellung festgelegt werden:

- **Alle Zeichen folgen Ausdrücke durch Leerzeichen ersetzen**
- **Ersetzen leerer Zeichen folgen Konstanten durch Leerzeichen**

Um das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /Azure SQL-Verhalten zu verwenden, wählen Sie **aktuelle Syntax beibehalten**aus.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Aktuelle Syntax beibehalten|
|Optimistisch|Aktuelle Syntax beibehalten|
|Vollständig|Alle Zeichen folgen Ausdrücke durch Leerzeichen ersetzen|

### <a name="convert-and-cast-binary-string-conversion"></a>Konvertieren und Umwandeln der binären Zeichen folgen Konvertierung

Die Konvertierung von Binär Werten in Zahlen kann unterschiedliche Werte auf verschiedenen Plattformen zurückgeben. Beispielsweise gibt auf x86-Prozessoren `CONVERT(integer, 0x00000100)` `65536` in ASE zurück, aber `256` in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Die ASE gibt abhängig von der Byte Reihenfolge auch andere Werte zurück.

Verwenden Sie diese Einstellung, um zu steuern, wie SSMA konvertiert `CONVERT` und `CAST` Ausdrücke, die binäre Werte enthalten:

- Wählen Sie **einfache Konvertierung** aus, um die Ausdrücke ohne Warnungen oder Korrekturen zu konvertieren. Verwenden Sie diese Einstellung, wenn Sie wissen, dass der ASE-Server eine Byte Reihenfolge aufweist, die keine Änderungen des Binär Werts erfordert.
- Wählen Sie **konvertieren und korrigieren** aus, damit SSMA die Ausdrücke für die Verwendung in konvertiert und korrigiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Die Byte Reihenfolge in Literalkonstanten wird umgekehrt. Alle anderen Binär Werte (z. b. binäre Variablen und Spalten) werden mit Fehlern markiert. Verwenden Sie diesen Wert, wenn Sie wissen, dass der ASE-Server eine Byte Reihenfolge aufweist, die Änderungen an Binär Werten erfordert.

Wählen Sie **konvertieren und mit Warnung markieren** aus, damit die Ausdrücke von SSMA konvertiert und korrigiert werden, und markieren Sie alle konvertierten Ausdrücke mit Warn Kommentaren.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Konvertieren und Markierung mit Warnung|
|Optimistisch|Einfache Konvertierung|
|Vollständig|Konvertieren und korrigieren|

### <a name="dynamic-sql"></a>Dynamische SQL-Anweisungen

Verwenden Sie diese Einstellung, um den Typ der Meldung (Warnung oder Fehler) anzugeben, die SSMA im **Ausgabe** -oder **Fehlerliste** Bereich anzeigt, wenn im ASE-Code dynamischer SQL-Code gefunden wird.

- Wenn Sie **konvertieren und mit Warnung markieren**auswählen, konvertiert SSMA das dynamische SQL und kennzeichnet die Anweisungen mit Warn Kommentaren.
- Wenn Sie **mit Fehler markieren**auswählen, wird die Konvertierung von SSMA übersprungen und die Anweisungen mit den Fehler Kommentaren markiert.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Konvertieren und Markierung mit Warnung|
|Optimistisch|Konvertieren und Markierung mit Warnung|
|Vollständig|Mit Fehler markieren|

### <a name="equality-check-conversion"></a>Konvertierung der Gleichheits Überprüfung

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Wenn in/Azure SQL die `ANSI_NULLS` Einstellung auf ON festgelegt ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt/Azure SQL zurück, `UNKNOWN` Wenn ein Gleichheits Vergleich einen `NULL` Wert enthält. Wenn auf `ANSI_NULLS` Off fest steht, geben Gleichheits Vergleiche, die Werte enthalten, `NULL` true zurück, wenn die verglichene Spalte und der Ausdruck oder zwei Ausdrücke beide sind `NULL` Standardmäßig verhalten sich ( `ANSINULL OFF` ) SAP ASE-Gleichheits Vergleiche wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /Azure SQL mit `ANSI_NULLS OFF` .

- Wenn Sie **einfache Konvertierung**auswählen, konvertiert SSMA den ASE-Code in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL-Syntax von/Azure, ohne dass zusätzliche Werte überprüft werden `NULL` . Verwenden Sie diese Einstellung, wenn `ANSI_NULLS` `OFF` in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /Azure SQL ist oder wenn Sie Übereinstimmungs Vergleiche pro Fall überarbeiten möchten.
- Wenn Sie **NULL-Werte in Erwägung gezogen**auswählen, werden von SSMA `NULL` mithilfe der Klauseln und Überprüfungen auf Werte hinzugefügt `IS NULL` `IS NOT NULL` .

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Einfache Konvertierung|
|Optimistisch|Einfache Konvertierung|
|Vollständig|NULL-Werte beachten|

### <a name="format-strings"></a>Formatzeichenfolgen

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Azure SQL unterstützt das `format_string` -Argument nicht mehr in `PRINT` -und- `RAISERROR` Anweisungen. Das `format_string` Argument, das ersetzbare Parameter direkt in die Zeichenfolge eingefügt werden darf, und dann die Parameter zur Laufzeit ersetzt werden. Stattdessen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erfordert die vollständige Zeichenfolge entweder mithilfe eines Zeichenfolgenliterals oder mithilfe einer Zeichenfolge, die mit einer Variablen erstellt wurde. Weitere Informationen finden Sie im Thema " [Print ( [!INCLUDE[tsql](../../includes/tsql-md.md)] )](../../t-sql/language-elements/print-transact-sql.md) ".

Wenn SSMA auf ein `format_string` Argument stößt, kann es entweder mithilfe der Variablen ein Zeichenfolgenliteralzeichen erstellen oder eine neue Variable erstellen und mithilfe dieser Variablen eine Zeichenfolge erstellen.

- Wählen Sie zum Verwenden eines Zeichenfolgenliterals für die `PRINT` Funktionen und die Option `RAISERROR` **neue Zeichenfolge**

    Wenn in diesem Modus eine Print-oder RAISERROR-Anweisung keine Platzhalter und lokalen Variablen verwendet, bleibt die Anweisung unverändert. Doppelte Prozentzeichen (%%) werden in druckzeichenfolgenliteralen in ein einzelnes Prozentzeichen in% geändert.

    Wenn eine Print-oder RAISERROR-Anweisung Platzhalter und eine oder mehrere lokale Variablen verwendet, z. b. im folgenden Beispiel:

    ```sql
    PRINT 'Total: %1!%%', @percent
    ```

    SSMA konvertiert sie in die folgende Syntax:

    ```sql
    PRINT 'Total: '+ CAST(@percent AS varchar(max)) + '%'
    ```

    Wenn `format_string` eine Variable ist, z. b. in der folgenden-Anweisung:  

    ```sql
    PRINT @fmt, @arg1, @arg2
    ```

    SSMA kann keine einfache Zeichen folgen Konvertierung durchführen und muss eine neue Variable erstellen:

    ```sql
    DECLARE @print_format_1 varchar(max)
    SET @print_format_1 =
        REPLACE (@fmt, '%%', '%')
    SET @print_format_1 =
        REPLACE (@print_format_1, '%1!',
        CAST (@arg1 AS varchar(max)))
    SET @print_format_1 =
        REPLACE (@print_format_1, '%2!',
        CAST (@arg2 AS varchar(max)))
    PRINT @print_format_1
    ```

    Bei Verwendung von **Create new String** Mode geht SSMA davon aus, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Option `CONCAT_NULL_YIELDS_NULL` ist `OFF` . Daher prüft SSMA nicht, ob NULL-Argumente verwendet werden.

- Wenn SSMA für jede `PRINT` -und-Anweisung eine neue Variable erstellen `RAISERROR` und diese Variable dann für den Zeichen folgen Wert verwenden soll, wählen Sie **neue Variable erstellen**aus.

    Wenn in diesem Modus eine `PRINT` -oder `RAISERROR` -Anweisung keine Platzhalter und lokalen Variablen verwendet, ersetzt SSMA alle doppelten Prozentzeichen ( `%%` ) durch einzelne Prozentzeichen, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /Azure SQL-Syntax einzuhalten.

    Wenn eine `PRINT` `RAISERROR` -oder-Anweisung Platzhalter und eine oder mehrere lokale Variablen verwendet, z. b. im folgenden Beispiel:

    ```sql
    PRINT 'Total: %1!%%', @percent
    ```

    SSMA konvertiert sie in die folgende Syntax:

    ```sql
    DECLARE @print_format_1 varchar(max)
    SET @print_format_1 = 'Total: %1!%'
    SET @print_format_1 =
        REPLACE (@print_format_1, '%1!',
        ISNULL(CAST (@percent AS VARCHAR(max)), ''))
    PRINT @print_format_1
    ```

    Wenn `format_string` eine Variable ist, z. b. in der folgenden-Anweisung:

    ```sql
    PRINT @fmt, @arg1, @arg2
    ```

    SSMA erstellt wie folgt eine neue Variable und überprüft in jedem Argument nach NULL-Werten:

    ```sql
    DECLARE @print_format_1 varchar(max)
    SET @print_format_1 =
        REPLACE (@fmt, '%%', '%')
    SET @print_format_1 =
        REPLACE (@print_format_1, '%1!',
        ISNULL(CAST (@arg1 AS varchar(max)),''))
    SET @print_format_1 =
        REPLACE (@print_format_1, '%2!',
        ISNULL(CAST (@arg2 AS varchar(max)),''))
    PRINT @print_format_1
    ```

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Neue Zeichenfolge erstellen|
|Optimistisch|Neue Zeichenfolge erstellen|
|Vollständig|Neue Variable erstellen|

### <a name="insert-an-explicit-value-into-a-timestamp-column"></a>Einfügen eines expliziten Werts in eine Zeitstempel-Spalte

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Azure SQL unterstützt nicht das Einfügen von expliziten Werten in eine Zeitstempel-Spalte.

- Um Zeitstempel-Spalten aus- `INSERT` Anweisungen auszuschließen, wählen Sie **Spalte ausschließen**aus.
- Wenn Sie eine Fehlermeldung jedes Mal ausdrucken möchten, wenn eine Zeitstempel-Spalte in einer- `INSERT` Anweisung vorliegt, wählen Sie **mit Fehler markieren**aus. In diesem Modus werden `INSERT` Anweisungen nicht konvertiert und mit Fehler Kommentaren markiert.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Spalte ausschließen|
|Optimistisch|Spalte ausschließen|
|Vollständig|Mit Fehler markieren|

### <a name="store-temporary-objects-defined-in-procedures"></a>In Prozeduren definierte temporäre Objekte speichern

Diese Einstellung gibt an, ob die in den Prozeduren angezeigten temporären Objekt Definitionen während der Konvertierung in den Quell Metadaten gespeichert werden sollen.

- Wählen Sie **Ja** aus, um Metadaten zu speichern.
- Wählen Sie **Nein** aus, wenn die Objekte nicht gespeichert werden müssen.

|Mode|Wert|
|-|-|
|Standard|Ja|
|Optimistisch|Ja|
|Vollständig|Nein|

### <a name="proxy-table-conversion"></a>Konvertieren von Proxy Tabellen

Gibt an, ob ASE-Proxy Tabellen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /Azure SQL-Tabellen konvertiert werden oder nicht konvertiert werden und der Code mit Fehler Kommentaren markiert ist.

- Wählen Sie **konvertieren** aus, um Proxy Tabellen in reguläre Tabellen zu konvertieren.
- Wählen Sie **mit Fehler markieren** aus, um den Proxy Tabellen Code einfach mit Fehler Kommentaren zu markieren.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Mit Fehler markieren|
|Optimistisch|Mit Fehler markieren|
|Vollständig|Mit Fehler markieren|

### <a name="raiserror-base-message-number"></a>RAISERROR-Basis Nachrichtennummer

ASE-Benutzer Nachrichten werden in jeder Datenbank gespeichert. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Benutzer Nachrichten werden zentral gespeichert und über die-Katalog Sicht zur Verfügung gestellt `sys.messages` . Außerdem beginnen ASE-Benutzer Nachrichten bei `20000` , aber [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehlermeldungen beginnen bei `50001` .

Diese Einstellung gibt die Zahl an, die der ASE-Benutzer Nachrichtennummer hinzugefügt wird, um Sie in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Benutzer Nachricht zu konvertieren. Wenn Ihre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Benutzer Meldungen in der- `sys.messages` Katalog Sicht enthalten, müssen Sie diese Zahl möglicherweise in einen höheren Wert ändern. Dies ist der Fall, wenn die konvertierten Nachrichtennummern nicht mit vorhandenen Nachrichtennummern in Konflikt stehen.

Beachten Sie Folgendes:
  
- ASE-Nachrichten im Bereich `17000` - `19999` stammen aus der `sysmessages` Systemtabelle und werden nicht konvertiert.
- Wenn die Nachrichtennummer, auf die in der-Anweisung verwiesen wird `RAISERROR` , eine Konstante ist, fügt SSMA der Konstante die Basis Nachrichtennummer hinzu, um die neue Benutzer Nachrichtennummer zu ermitteln.
- Wenn die Nachrichtennummer, auf die verwiesen wird, eine Variable oder ein Ausdruck ist, erstellt SSMA eine lokale zwischen Variable.
- Im **optimistischen Modus**geht SSMA davon aus, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Option `CONCAT_NULL_YIELDS_NULL` ist, `OFF` und führt keine Überprüfungen auf `NULL` Argumente aus.
- Im **vollständigen Modus**überprüft SSMA auf `NULL` Argumente.
- `RAISERROR` with- `arg-list` Argument wird nicht konvertiert.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|30001|
|Optimistisch|30001|
|Vollständig|30001|

### <a name="system-objects"></a>Systemobjekte

Verwenden Sie diese Einstellung, um den Typ der Meldung (Warnung oder Fehler) anzugeben, die SSMA im **Ausgabe** -oder **Fehlerliste** Bereich anzeigt, wenn die Systemobjekte der ASE verwendet werden.

- Wenn Sie **konvertieren und mit Warnung markieren**auswählen, konvertiert SSMA Verweise auf Systemobjekte und markiert Anweisungen mit Warn Kommentaren.
- Wenn Sie **mit Fehler markieren**auswählen, werden von SSMA keine Verweise auf Systemobjekte konvertiert, und es werden Anweisungen mit Fehler Kommentaren markiert.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Konvertieren und Markierung mit Warnung|
|Optimistisch|Konvertieren und Markierung mit Warnung|
|Vollständig|Mit Fehler markieren|

### <a name="unresolved-identifiers"></a>Nicht aufgelöste Bezeichner

Verwenden Sie diese Einstellung, um den Typ der Meldung (Warnung oder Fehler) anzugeben, die SSMA im **Ausgabe** -oder **Fehlerliste** Bereich anzeigt, wenn ein Bezeichner nicht aufgelöst werden kann.

- Wenn Sie **konvertieren und mit Warnung markieren**auswählen, versucht SSMA, Verweise auf nicht aufgelöste Bezeichner zu konvertieren, und es werden Anweisungen mit Warn Kommentaren markiert.
- Wenn Sie **mit Fehler markieren**auswählen, werden Verweise nicht von SSMA in nicht aufgelöste Bezeichner konvertiert, und es werden Anweisungen mit Fehler Kommentaren markiert.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Konvertieren und Markierung mit Warnung|
|Optimistisch|Konvertieren und Markierung mit Warnung|
|Vollständig|Mit Fehler markieren|

## <a name="system-functions-section"></a>Abschnitt "System Funktionen"

### <a name="charindex-function"></a>CHARINDEX-Funktion

In ASE `CHARINDEX` gibt `NULL` nur dann zurück, wenn alle Eingabe Ausdrücke sind `NULL` . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Azure SQL gibt zurück, `NULL` Wenn ein Eingabe Ausdruck ist `NULL` .

- Um das ASE-Verhalten zu verwenden, wählen Sie **Funktion ersetzen**aus. Alle Aufrufe `CHARINDEX` der Funktion werden durch einen Aufruf von oder einer `CHARINDEX_VARCHAR`  `CHARINDEX_NVARCHAR` benutzerdefinierten Funktion basierend auf dem Typ der Parameter, die in der Benutzerdatenbank unter dem Schema Namen erstellt wurden `s2ss` , ersetzt, um das SAP ASE-Verhalten zu emulieren.
- Um das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /Azure SQL-Verhalten zu verwenden, wählen Sie **aktuelle Syntax beibehalten**aus.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Aktuelle Syntax beibehalten|
|Optimistisch|Aktuelle Syntax beibehalten|
|Vollständig|Replace-Funktion|
  
### <a name="datalength-function"></a>DATALENGTH-Funktion

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Azure SQL und ASE unterscheiden sich in dem Wert, der von der Funktion zurückgegeben `DATALENGTH` wird, wenn der Wert ein einzelnes Leerzeichen ist. In diesem Fall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt/Azure SQL zurück, `0` und ASE gibt zurück `1` .

- Um das ASE-Verhalten zu verwenden, wählen Sie **Funktion ersetzen**aus. Alle Aufrufe der `DATALENGTH` Funktion werden durch einen `CASE` Ausdruck ersetzt, um das SAP ASE-Verhalten zu emulieren.
- Um das Standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verhalten von/Azure SQL zu verwenden, wählen Sie **aktuelle Syntax beibehalten**aus.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Aktuelle Syntax beibehalten|
|Optimistisch|Aktuelle Syntax beibehalten|
|Vollständig|Replace-Funktion|

### <a name="index_col-function"></a>INDEX_COL-Funktion

ASE unterstützt ein optionales `user_id` Argument für die `INDEX_COL` Funktion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ./Azure SQL unterstützt dieses Argument jedoch nicht. Wenn Sie das- `user_id` Argument verwenden, kann diese Funktion nicht in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /Azure SQL-Syntax konvertiert werden.

- Um das ASE-Verhalten zu verwenden, wählen Sie **Funktion konvertieren**aus. Wenn der Code das `user_id` Argument enthält, zeigt SSMA einen Fehler an.
- Wenn Sie bei jedem Auftreten einer Fehlermeldung eine Fehlermeldung anzeigen möchten `INDEX_COL` , wählen Sie **mit Fehler markieren**aus. SSMA konvertiert keine Verweise auf die Funktion und markiert die Anweisung mit Fehler Kommentaren.

|Mode|Wert|
|-|-|
|Standard|Mit Fehler markieren|
|Optimistisch|Mit Fehler markieren|
|Vollständig|Mit Fehler markieren|

### <a name="index_colorder-function"></a>INDEX_COLORDER-Funktion

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Azure SQL hat keine `INDEX_COLORDER` Systemfunktion.

- Um das ASE-Verhalten zu verwenden, wählen Sie **Funktion konvertieren**aus. Alle Aufrufe `INDEX_COLORDER` der Funktion werden durch einen Aufruf einer benutzerdefinierten Funktion mit demselben Namen ersetzt `INDEX_COLORDER` (erstellt in der Benutzerdatenbank unter dem Schema Namen `s2ss` ), die das SAP ASE-Verhalten emuliert.
- Wenn Sie bei jedem Auftreten einer Fehlermeldung eine Fehlermeldung ausgeben möchten `INDEX_COLORDER` , wählen Sie **mit Fehler markieren**aus. SSMA konvertiert keine Verweise auf die Funktion und markiert die Anweisung mit Fehler Kommentaren.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Mit Fehler markieren|
|Optimistisch|Mit Fehler markieren|
|Vollständig|Mit Fehler markieren|

### <a name="left-and-right-functions"></a>Left-und Right-Funktionen

`LEFT` die `RIGHT` Funktionen und in ASE Verhalten sich für den Parameter für negative Länge anders.

- Um das ASE-Verhalten zu verwenden, wählen Sie **Funktion ersetzen**aus. Der length-Parameter wird dann durch einen `CASE` Ausdruck ersetzt, der `NULL` für einen negativen Wert zurückgibt.
- Um das SQL Server Verhalten zu verwenden, wählen Sie **aktuelle Syntax beibehalten**aus.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Aktuelle Syntax beibehalten|
|Optimistisch|Aktuelle Syntax beibehalten|
|Vollständig|Replace-Funktion|

> [!NOTE]
> Wenn der length-Parameter ein Literalwert und kein komplexer Ausdruck ist, wird der Längen Wert immer durch ersetzt, `NULL` unabhängig von der Projekteinstellung.

### <a name="next_identity-function"></a>NEXT_IDENTITY-Funktion

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Azure SQL hat keine `NEXT_IDENTITY` Systemfunktion.

- Um das ASE-Verhalten zu verwenden, wählen Sie **Funktion konvertieren**aus. Alle Aufrufe `NEXT_IDENTITY` der Funktion werden durch einen Ausdruck ersetzt `(IDENT_CURRENT(parameter Value) + IDENT_INCR(parameter Value)` , der das SAP ASE-Verhalten emuliert.
- Wenn Sie bei jedem Auftreten einer Fehlermeldung eine Fehlermeldung ausgeben möchten `NEXT_IDENTITY` , wählen Sie **mit Fehler markieren**aus. SSMA konvertiert keine Verweise auf die Funktion und markiert die Anweisung mit Fehler Kommentaren.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Mit Fehler markieren|
|Optimistisch|Mit Fehler markieren|
|Vollständig|Mit Fehler markieren|

**Standardmodus/optimistischer/Vollmodus:** Mit Fehler markieren

### <a name="patindex-function"></a>PATINDEX-Funktion

Gibt an, ob die `PATINDEX` Funktion entsprechend dem SAP ASE-Verhalten konvertiert werden soll. Der Punkt ist, dass die ASE nachfolgende Leerzeichen in einem Suchmuster schneidet. Die Problem Umgehung besteht darin, eine Umwandlung eines Wert Ausdrucks in einen Datentyp mit fester Länge mit einer maximalen Genauigkeit und einer Apply- `rtrim` Funktion auf das Suchmuster vorzunehmen.

- Um das ASE-Verhalten zu verwenden, wählen Sie **verwenden**.  
- Wenn Sie das Standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verhalten von/Azure SQL verwenden möchten, wählen Sie **nicht verwenden**aus.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Nicht verwenden|
|Optimistisch|Nicht verwenden|
|Vollständig|Verwendung|

### <a name="replicate-function"></a>REPLICATE-Funktion

Die- `REPLICATE` Funktion wiederholt eine Zeichenfolge so oft wie angegeben. Wenn Sie in ASE angeben, dass die Zeichenfolge NULL Mal wiederholt werden soll, ist das Ergebnis `NULL` . In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /Azure SQL ist das Ergebnis eine leere Zeichenfolge.

- Um das ASE-Verhalten zu verwenden, wählen Sie **Funktion ersetzen**aus. Alle Aufrufe `REPLICATE` der Funktion werden durch einen Aufruf von oder einer `REPLICATE_VARCHAR` `REPLICATE_NVARCHAR` benutzerdefinierten Funktion basierend auf dem Typ der Parameter, die in der Benutzerdatenbank unter dem Schema Namen erstellt wurden `s2ss` , ersetzt, um das SAP ASE-Verhalten zu emulieren.
- Um das Standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verhalten von/Azure SQL zu verwenden, wählen Sie **Funktion ersetzen**aus.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Replace-Funktion|
|Optimistisch|Replace-Funktion|
|Vollständig|Replace-Funktion|

### <a name="trim-ltrim-rtrim-function"></a>Trim (LTrim, RTrim)-Funktion

Diese Einstellung gibt an, ob Aufrufe von `TRIM` `LTRIM` und `RTRIM` -Funktionen durch die SAP ASE-äquivalenten Syntax Funktionen ersetzt werden sollen, oder ob die aktuelle Syntax beibehalten werden soll. Die folgenden Optionen sind für diese spezielle Einstellung vorhanden:

- **Replace-Funktion**
- **Aktuelle Syntax beibehalten**

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Replace-Funktion|
|Optimistisch|Replace-Funktion|
|Vollständig|Replace-Funktion|

### <a name="substring-function"></a>SUBSTRING-Funktion

In ASE gibt die Funktion `SUBSTRING(expression, start, length)` zurück `NULL` , wenn ein Startwert größer als die Anzahl der Zeichen im Ausdruck ist, oder wenn die Länge 0 (null) ist. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /Azure SQL gibt der äquivalente Ausdruck eine leere Zeichenfolge zurück.

- Um das ASE-Verhalten zu verwenden, wählen Sie **Funktion ersetzen**aus. Alle Aufrufe `SUBSTRING` der Funktion werden durch einen Aufruf von `SUBSTRING_VARCHAR` oder oder `SUBSTRING_NVARCHAR` eine `SUBSTRING_VARBINARY` benutzerdefinierte Funktion basierend auf dem Typ der Parameter, die in der Benutzerdatenbank unter dem Schema Namen erstellt wurden `s2ss` , ersetzt, um das SAP ASE-Verhalten zu emulieren.
- Um das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /Azure SQL-Verhalten zu verwenden, wählen Sie **aktuelle Syntax beibehalten**aus.

Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:

|Mode|Wert|
|-|-|
|Standard|Aktuelle Syntax beibehalten|
|Optimistisch|Aktuelle Syntax beibehalten|
|Vollständig|Replace-Funktion|

## <a name="tables-section"></a>Tabellen Abschnitt

### <a name="add-primary-key"></a>Primärschlüssel hinzufügen

Erstellt einen neuen Primärschlüssel in der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Tabelle, wenn eine SAP ASE-Tabelle keinen Primärschlüssel oder eindeutigen Index aufweist.

|Mode|Wert|
|-|-|
|Standard|Nein|
|Optimistisch|Nein|
|Vollständig|Ja|

> [!NOTE]
> Wenn eine Verbindung mit Azure SQL besteht, ist dies standardmäßig **Ja** .

## <a name="see-also"></a>Weitere Informationen

[Referenz zur Benutzeroberfläche (SybaseToSQL)](../../ssma/sybase/user-interface-reference-sybasetosql.md)
