---
description: Projekteinstellungen (Konvertierung) (SybaseToSQL)
title: Projekteinstellungen (Konvertierung) (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: eeb80fa5-f530-4f21-beee-25f5a4b8ace6
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 61795be0d1f851792846f2ede8c38eca1f3801b0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468794"
---
# <a name="project-settings-conversion-sybasetosql"></a>Projekteinstellungen (Konvertierung) (SybaseToSQL)
Die Seite Konvertierung des Dialog Felds **Projekteinstellungen** enthält Einstellungen, die anpassen, wie SSMA die Syntax von Sybase Adaptive Server Enterprise (ASE) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Syntax konvertiert.  
  
Der Bereich Konvertierung ist in den Dialogfeldern **Projekteinstellungen** und **Standard Projekteinstellungen** verfügbar:  
  
-   Wenn Sie Einstellungen für alle SSMA-Projekte angeben möchten, wählen Sie **im Menü Extras** die **Option Standard Projekteinstellungen**aus, klicken Sie unten im linken Bereich auf **Allgemein** , und klicken Sie dann auf **Konvertierung**.  
  
-   Um Einstellungen für das aktuelle Projekt anzugeben, wählen Sie **im Menü Extras** die **Option Projekteinstellungen**aus, klicken Sie unten im linken Bereich auf **Allgemein** , und klicken Sie dann auf **Konvertierung**.  
  
## <a name="miscellaneous-options"></a>Sonstige Optionen  
**@@ERROR**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure und ASE verwenden andere Fehlercodes.  
  
Verwenden Sie diese Einstellung, um den Typ der Meldung (Warnung oder Fehler) anzugeben, die SSMA im Ausgabe-oder Fehlerliste Bereich anzeigt, wenn im ASE-Code auf **@ @ERROR ** verwiesen wird.  
  
-   Wenn Sie **konvertieren und mit Warnung markieren**auswählen, werden die Anweisungen von SSMA konvertiert und mit Warn Kommentaren markiert.  
  
-   Wenn Sie **mit Fehler markieren**auswählen, wird die Konvertierung von SSMA übersprungen und die Anweisungen mit den Fehler Kommentaren markiert.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus:** Konvertieren und Markierung mit Warnung  
  
**Vollständiger Modus:** Mit Fehler markieren  
  
**Konvertierung des LIKE-Operators**  
Gibt an, ob like-Operanden konvertiert werden, um das Verhalten von Sybase ASE zu erfüllen Der Punkt ist, dass Sybase nachfolgende Leerzeichen in einem like-Muster schneidet. Die Problem Umgehung besteht darin, eine Umwandlung eines Right-Ausdrucks in einen Datentyp mit fester Länge mit einer maximalen Genauigkeit vorzunehmen.  
  
-   Wählen Sie **einfache Konvertierung** aus, um die Ausdrücke ohne Korrektur zu konvertieren.  
  
-   Um das ASE-Verhalten zu verwenden, wählen Sie Umwandlung **in eine Fixed-Länge**  
  
Wenn Sie im Feld Modus einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus**: einfache Konvertierung  
  
**Vollständiger Modus**: Umwandlung in eine Länge mit fester Länge  
  
**konvertieren oder umwandeln leerer Zeichen folgen in numerische Typen**  
Gibt an, wie leere oder leere Zeichen folgen innerhalb von Convert-oder Cast-Ausdrücken mit einem numerischen Typ als Datentyp-Argument behandelt werden. Die folgenden Optionen sind für diese Einstellung verfügbar:  
  
-   Wählen Sie **einfache Konvertierung** aus, um die Ausdrücke ohne Korrektur zu konvertieren.  
  
-   Wenn eine **leere Zeichenfolge als** 0 (null) ausgewählt ist, wird der Zeichen folgen Parameter "{s}" durch Case LTrim (RTrim ({s})) ersetzt, wenn "" Then 0 else {s} End Expression  
  
Wenn Sie im Feld Modus einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus**: einfache Konvertierung  
  
**Vollständiger Modus**: leere Zeichenfolge als 0 (null)  
  
**Verkettung von NULL**  
Diese Einstellung gibt an, wie die Zeichen folgen Verkettung mit NULL konvertiert werden soll. Die folgenden Optionen können für diese spezielle Einstellung festgelegt werden:  
  
-   **Wrap mit IsNull-Funktion:** Wenn diese Option festgelegt ist, werden alle nicht Konstanten ' string_expression ' in der Verkettung mit IsNull (string_expression) umschließen, und Nullen werden durch eine leere Zeichenfolge ersetzt.  
  
-   **Aktuelle Syntax beibehalten**  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus:** Aktuelle Syntax beibehalten  
  
**Vollständiger Modus:** Wrap mit IsNull-Funktion  
  
**Konvertierung von leeren Zeichen folgen**  
Diese Einstellung gibt an, wie leere Zeichen folgen konvertiert werden. Die folgenden Optionen können für diese spezielle Einstellung festgelegt werden:  
  
-   **Alle Zeichen folgen Ausdrücke durch Leerzeichen ersetzen**  
  
-   **Ersetzen leerer Zeichen folgen Konstanten durch Leerzeichen**  
  
-   Um das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /SQL Azure-Verhalten zu verwenden, wählen Sie **aktuelle Syntax beibehalten**aus.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus:** Aktuelle Syntax beibehalten  
  
**Vollständiger Modus:** Alle Zeichen folgen Ausdrücke durch Leerzeichen ersetzen  
  
**Konvertieren und Umwandeln der binären Zeichen folgen Konvertierung**  
Die Konvertierung von Binär Werten in Zahlen kann unterschiedliche Werte auf verschiedenen Plattformen zurückgeben. Auf x86-Prozessoren gibt Convert (Integer, 0x00000100) z. b. 65536 in ASE und 256 in zurück [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Die ASE gibt abhängig von der Byte Reihenfolge auch andere Werte zurück.  
  
Verwenden Sie diese Einstellung, um zu steuern, wie SSMA Convert-und CASE-Ausdrücke konvertiert, die binäre Werte enthalten:  
  
-   Wählen Sie **einfache Konvertierung** aus, um die Ausdrücke ohne Warnungen oder Korrekturen zu konvertieren. Verwenden Sie diese Einstellung, wenn Sie wissen, dass der ASE-Server eine Byte Reihenfolge aufweist, die keine Änderungen des Binär Werts erfordert.  
  
-   Wählen Sie **konvertieren und korrigieren** aus, damit SSMA die Ausdrücke für die Verwendung in konvertiert und korrigiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Die Byte Reihenfolge in Literalkonstanten wird umgekehrt. Alle anderen Binär Werte (z. b. binäre Variablen und Spalten) werden mit Fehlern markiert. Verwenden Sie diesen Wert, wenn Sie wissen, dass der ASE-Server eine Byte Reihenfolge aufweist, die Änderungen an Binär Werten erfordert.  
  
-   Wählen Sie **konvertieren und mit Warnung markieren** aus, damit die Ausdrücke von SSMA konvertiert und korrigiert werden, und markieren Sie alle konvertierten Ausdrücke mit Warn Kommentaren.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus:** Konvertieren und Markierung mit Warnung  
  
**Optimistischer Modus:** Einfache Konvertierung  
  
**Vollständiger Modus:** Konvertieren und korrigieren  
  
**Dynamischer SQL-Code**  
Verwenden Sie diese Einstellung, um den Typ der Meldung (Warnung oder Fehler) anzugeben, die SSMA im Ausgabe-oder Fehlerliste Bereich anzeigt, wenn im ASE-Code dynamischer SQL-Code gefunden wird.  
  
-   Wenn Sie **konvertieren und mit Warnung markieren**auswählen, konvertiert SSMA das dynamische SQL und kennzeichnet die Anweisungen mit Warn Kommentaren.  
  
-   Wenn Sie **mit Fehler markieren**auswählen, wird die Konvertierung von SSMA übersprungen und die Anweisungen mit den Fehler Kommentaren markiert.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus:** Konvertieren und Markierung mit Warnung  
  
**Vollständiger Modus:** Mit Fehler markieren  
  
**Konvertierung der Gleichheits Überprüfung**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Wenn in/SQL Azure die ANSI_NULLS Einstellung auf ON festgelegt ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt/SQL Azure Unknown zurück, wenn ein Gleichheits Vergleich einen NULL-Wert enthält. Wenn ANSI_NULLS deaktiviert ist, geben Gleichheits Vergleiche, die NULL-Werte enthalten, true zurück, wenn die verglichene Spalte und der Ausdruck oder zwei Ausdrücke NULL sind. Standardmäßig verhalten sich Sybase-ASE-Gleichheits Vergleiche (ansinull off) wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /SQL Azure mit ANSI_NULLS off.  
  
-   Wenn Sie **einfache Konvertierung**auswählen, konvertiert SSMA den ASE-Code in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /SQL Azure-Syntax, ohne dass zusätzliche Überprüfungen für NULL-Werte durchgeführt werden. Verwenden Sie diese Einstellung, wenn ANSI_NULLS in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /SQL Azure deaktiviert ist, oder wenn Sie Gleichheits Vergleiche pro Fall überarbeiten möchten.  
  
-   Wenn Sie **NULL-Werte in Erwägung gezogen**auswählen, fügt SSMA mithilfe der Klauseln is NULL und is not NULL Überprüfungen auf NULL-Werte hinzu.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus:** Einfache Konvertierung  
  
**Vollständiger Modus:** NULL-Werte beachten  
  
**Format Zeichenfolgen**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Das *FORMAT_STRING* -Argument in den Print-und RAISERROR-Anweisungen wird von SQL Azure nicht mehr unterstützt. Die *FORMAT_STRING* -Variable unterstützte das direkte Platzieren von ersetzbaren Parametern in der Zeichenfolge und das anschließende ersetzen der Parameter zur Laufzeit. Stattdessen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erfordert die vollständige Zeichenfolge entweder mithilfe eines Zeichenfolgenliterals oder mithilfe einer Zeichenfolge, die mit einer Variablen erstellt wurde. Weitere Informationen finden Sie im Thema "Print ( [!INCLUDE[tsql](../../includes/tsql-md.md)] )" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Online Dokumentation.  
  
Wenn SSMA auf ein *FORMAT_STRING* Argument stößt, kann es entweder mithilfe der Variablen ein Zeichenfolgenliteralzeichen erstellen oder eine neue Variable erstellen und mithilfe dieser Variablen eine Zeichenfolge erstellen.  
  
-   Zum Verwenden eines Zeichenfolgenliterals für Druck-und RAISERROR-Funktionen wählen Sie **neue Zeichenfolge erstellen**  
  
    Wenn in diesem Modus eine Print-oder RAISERROR-Anweisung keine Platzhalter und lokalen Variablen verwendet, bleibt die Anweisung unverändert. Doppelte Prozentzeichen (%%) werden in druckzeichenfolgenliteralen in ein einzelnes Prozentzeichen in% geändert.  
  
    Wenn eine Print-oder RAISERROR-Anweisung Platzhalter und eine oder mehrere lokale Variablen verwendet, z. b. im folgenden Beispiel:  
  
    ```  
    PRINT 'Total: %1!%%', @percent  
    ```  
    SSMA konvertiert sie in die folgende Syntax:  
  
    ```  
    PRINT 'Total: '+ CAST(@percent AS varchar(max)) + '%'  
    ```  
    Wenn *FORMAT_STRING* eine Variable ist, z. b. in der folgenden Anweisung:  
  
    ```  
    PRINT @fmt, @arg1, @arg2  
    ```  
    SSMA kann keine einfache Zeichen folgen Konvertierung durchführen und muss eine neue Variable erstellen:  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1  =   
        REPLACE (@fmt, '%%', '%')  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        CAST (@arg1 AS varchar(max)))  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%2!',   
        CAST (@arg2 AS varchar(max)))  
    PRINT @print_format_1  
    ```  
    Bei Verwendung von **Create new String** Mode geht SSMA davon aus, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Option CONCAT_NULL_YIELDS_NULL deaktiviert ist. Daher prüft SSMA nicht, ob NULL-Argumente verwendet werden.  
  
-   Um SSMA für jede Print-und RAISERROR-Anweisung eine neue Variable zu erstellen und diese Variable anschließend für den Zeichen folgen Wert zu verwenden, wählen Sie **neue Variable erstellen**aus.  
  
    Wenn in diesem Modus eine Print-oder RAISERROR-Anweisung keine Platzhalter und lokalen Variablen verwendet, ersetzt SSMA alle doppelten Prozentzeichen (%%). mit einem Prozentzeichen, das mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /SQL Azure-Syntax übereinstimmt.  
  
    Wenn eine Print-oder RAISERROR-Anweisung Platzhalter und eine oder mehrere lokale Variablen verwendet, z. b. im folgenden Beispiel:  
  
    ```  
    PRINT 'Total: %1!%%', @percent  
    ```  
    SSMA konvertiert sie in die folgende Syntax:  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1 = 'Total: %1!%'  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        ISNULL(CAST (@percent AS VARCHAR(max)), ''))  
    PRINT @print_format_1  
    ```  
    Wenn *FORMAT_STRING* eine Variable ist, z. b. in der folgenden Anweisung:  
  
    ```  
    PRINT @fmt, @arg1, @arg2  
    ```  
    SSMA erstellt wie folgt eine neue Variable und überprüft in jedem Argument nach NULL-Werten:  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1  =   
        REPLACE (@fmt, '%%', '%')  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        ISNULL(CAST (@arg1 AS varchar(max)),''))  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%2!',   
        ISNULL(CAST (@arg2 AS varchar(max)),''))  
    PRINT @print_format_1  
    ```  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus:** Neue Zeichenfolge erstellen  
  
**Vollständiger Modus:** Neue Variable erstellen  
  
**Einfügen eines expliziten Werts in eine Zeitstempel-Spalte**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure unterstützt nicht das Einfügen von expliziten Werten in eine Zeitstempel-Spalte.  
  
-   Um Zeitstempel-Spalten aus INSERT-Anweisungen auszuschließen, wählen Sie **Spalte ausschließen**aus.  
  
-   Wenn Sie eine Fehlermeldung jedes Mal ausdrucken möchten, wenn eine Zeitstempel-Spalte in einer INSERT-Anweisung vorliegt, wählen Sie **mit Fehler markieren**aus. In diesem Modus werden INSERT-Anweisungen nicht konvertiert und mit Fehler Kommentaren markiert.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus:** Spalte ausschließen  
  
**Vollständiger Modus:** Mit Fehler markieren  
  
**In Prozeduren definierte temporäre Objekte speichern**  
Diese Einstellung gibt an, ob die in den Prozeduren angezeigten temporären Objekt Definitionen während der Konvertierung in den Quell Metadaten gespeichert werden sollen.  
  
-   Wählen Sie **Ja**  aus, um Metadaten zu speichern.  
  
-   Wählen Sie **Nein**  aus, wenn die Objekte nicht gespeichert werden müssen.  
  
**Standardmodus/optimistischer Modus:** Zwar  
  
**Vollständiger Modus:** Nein  
  
**Konvertieren von Proxy Tabellen**  
Gibt an, ob ASE-Proxy Tabellen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /SQL Azure Tabellen konvertiert werden oder nicht konvertiert werden und der Code mit Fehler Kommentaren markiert ist.  
  
-   Wählen Sie **konvertieren** aus, um Proxy Tabellen in reguläre Tabellen zu konvertieren.  
  
-   Wählen Sie **mit Fehler markieren** aus, um den Proxy Tabellen Code einfach mit Fehler Kommentaren zu markieren.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer/Vollmodus:** Mit Fehler markieren  
  
**RAISERROR-Basis Nachrichtennummer**  
ASE-Benutzer Nachrichten werden in jeder Datenbank gespeichert. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Benutzer Nachrichten werden zentral gespeichert und über die **sys. Messages** -Katalog Sicht verfügbar gemacht. Außerdem beginnen ASE-Benutzer Nachrichten um 20000, aber [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehlermeldungen beginnen bei 50001.  
  
Diese Einstellung gibt die Zahl an, die der ASE-Benutzer Nachrichtennummer hinzugefügt wird, um Sie in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Benutzer Nachricht zu konvertieren. Wenn Ihre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Benutzer Meldungen in der **sys. Messages** -Katalog Sicht enthalten, müssen Sie diese Zahl möglicherweise in einen höheren Wert ändern. Dies ist der Fall, wenn die konvertierten Nachrichtennummern nicht mit vorhandenen Nachrichtennummern in Konflikt stehen.  
  
Beachten Sie Folgendes:  
  
-   ASE-Nachrichten im Bereich 17000-19999 stammen aus der sysmess-Systemtabelle und werden nicht konvertiert.  
  
-   Wenn die Nachrichtennummer, auf die in der RAISERROR-Anweisung verwiesen wird, eine Konstante ist, fügt SSMA der Konstante die Basis Nachrichtennummer hinzu, um die neue Benutzer Nachrichtennummer zu ermitteln.  
  
-   Wenn die Nachrichtennummer, auf die verwiesen wird, eine Variable oder ein Ausdruck ist, erstellt SSMA eine lokale zwischen Variable.  
  
-   Im optimistischen Modus geht SSMA davon aus, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Option CONCAT_NULL_YIELDS_NULL deaktiviert ist, und führt keine Überprüfungen auf NULL-Argumente aus.  
  
-   Im vollständigen Modus überprüft SSMA auf NULL-Argumente.  
  
-   RAISERROR mit der ErrorData- *Liste* wurde nicht konvertiert.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer/Vollmodus:** 30001  
  
**System Objekte**  
Verwenden Sie diese Einstellung, um den Typ der Meldung (Warnung oder Fehler) anzugeben, die SSMA im Ausgabe-oder Fehlerliste Bereich anzeigt, wenn die Systemobjekte der ASE verwendet werden.  
  
-   Wenn Sie **konvertieren und mit Warnung markieren**auswählen, konvertiert SSMA Verweise auf Systemobjekte und markiert Anweisungen mit Warn Kommentaren.  
  
-   Wenn Sie **mit Fehler markieren**auswählen, werden von SSMA keine Verweise auf Systemobjekte konvertiert, und es werden Anweisungen mit Fehler Kommentaren markiert.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus:** Konvertieren und Markierung mit Warnung  
  
**Vollständiger Modus:** Mit Fehler markieren  
  
**Nicht aufgelöste Bezeichner**  
Verwenden Sie diese Einstellung, um den Typ der Meldung (Warnung oder Fehler) anzugeben, die SSMA im Ausgabe-oder Fehlerliste Bereich anzeigt, wenn ein Bezeichner nicht aufgelöst werden kann.  
  
-   Wenn Sie **konvertieren und mit Warnung markieren**auswählen, versucht SSMA, Verweise auf nicht aufgelöste Bezeichner zu konvertieren, und es werden Anweisungen mit Warn Kommentaren markiert.  
  
-   Wenn Sie **mit Fehler markieren**auswählen, werden Verweise nicht von SSMA in nicht aufgelöste Bezeichner konvertiert, und es werden Anweisungen mit Fehler Kommentaren markiert.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus:** Konvertieren und Markierung mit Warnung  
  
**Vollständiger Modus:** Mit Fehler markieren  
  
## <a name="system-function-options"></a>System Funktions Optionen  
**CHARINDEX-Funktion**  
In ASE gibt CHARINDEX nur dann NULL zurück, wenn alle Eingabe Ausdrücke NULL sind. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure gibt NULL zurück, wenn ein Eingabe Ausdruck NULL ist.  
  
-   Um das ASE-Verhalten zu verwenden, wählen Sie **Funktion ersetzen**aus. Alle Aufrufe der CHARINDEX-Funktion werden durch einen Aufruf von entweder CHARINDEX_VARCHAR oder CHARINDEX_NVARCHAR benutzerdefinierten Funktion basierend auf dem Typ der Parameter (erstellt in der Benutzerdatenbank mit dem Schema Namen 2SS) ersetzt, um das Verhalten der Sybase-ASE zu emulieren.  
  
-   Um das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /SQL Azure-Verhalten zu verwenden, wählen Sie **aktuelle Syntax beibehalten**aus.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus:** Aktuelle Syntax beibehalten  
  
**Vollständiger Modus:** Replace-Funktion  
  
**DATALENGTH-Funktion**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /SQL Azure und ASE unterscheiden sich in dem Wert, der von der DATALENGTH-Funktion zurückgegeben wird, wenn der Wert ein einzelnes Leerzeichen ist. In diesem Fall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt/SQL Azure 0 zurück, und ASE gibt 1 zurück.  
  
-   Um das ASE-Verhalten zu verwenden, wählen Sie **Funktion ersetzen**aus. Alle Aufrufe der DATALENGTH-Funktion werden durch den Case-Ausdruck ersetzt, um das Verhalten der Sybase ASE zu emulieren.  
  
-   Um das Standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -/SQL Azure Verhalten zu verwenden, wählen Sie **aktuelle Syntax beibehalten**aus.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus:** Aktuelle Syntax beibehalten  
  
**Vollständiger Modus:** Replace-Funktion  
  
**INDEX_COL-Funktion**  
ASE unterstützt ein optionales *user_id* Argument für die INDEX_COL-Funktion. Allerdings [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt/SQL Azure dieses Argument nicht. Wenn Sie das *user_id* -Argument verwenden, kann diese Funktion nicht in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /SQL Azure-Syntax konvertiert werden.  
  
-   Um das ASE-Verhalten zu verwenden, wählen Sie **Funktion konvertieren**aus. Wenn der Code das *user_id* -Argument enthält, zeigt SSMA einen Fehler an.  
  
-   Wenn Sie bei jedem Auftreten INDEX_COL eine Fehlermeldung anzeigen möchten, wählen Sie **mit Fehler markieren**aus. SSMA konvertiert keine Verweise auf die Funktion und markiert die Anweisung mit Fehler Kommentaren.  
  
**Standardmodus/optimistischer/Vollmodus:** Mit Fehler markieren  
  
**INDEX_COLORDER-Funktion**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure verfügt nicht über eine INDEX_COLORDER Systemfunktion.  
  
-   Um das ASE-Verhalten zu verwenden, wählen Sie **Funktion konvertieren**aus. Alle Aufrufe an INDEX_COLORDER Funktion werden durch einen Aufruf einer benutzerdefinierten Funktion mit demselben Namen ersetzt INDEX_COLORDER (erstellt in der Benutzerdatenbank unter dem Schema Namen 2SS), der das Verhalten der Sybase-ASE emuliert.  
  
-   Wenn Sie bei jedem Auftreten INDEX_COLORDER eine Fehlermeldung ausgeben möchten, wählen Sie **mit Fehler markieren**aus. SSMA konvertiert keine Verweise auf die Funktion und markiert die Anweisung mit Fehler Kommentaren.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer/Vollmodus:** Mit Fehler markieren  
  
**Left-und Right-Funktionen**  
Die Funktionen "Left" und "Right" in Sybase Verhalten sich bei negativen Längen Parametern anders.  
  
-   Um das ASE-Verhalten zu verwenden, wählen Sie **Funktion ersetzen**aus. Der length-Parameter wird dann durch einen Case-Ausdruck ersetzt, der NULL für einen negativen Wert zurückgibt.  
  
-   Um das SQL Server Verhalten zu verwenden, wählen Sie **aktuelle Syntax beibehalten** aus.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus:** Aktuelle Syntax beibehalten  
  
**Vollständiger Modus:** Replace-Funktion  
  
> [!NOTE]  
> Wenn der length-Parameter ein Literalwert und kein komplexer Ausdruck ist, wird der Längen Wert unabhängig von der Projekteinstellung immer durch Null ersetzt.  
  
**NEXT_IDENTITY-Funktion**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/SQL Azure verfügt nicht über eine NEXT_IDENTITY Systemfunktion.  
  
-   Um das ASE-Verhalten zu verwenden, wählen Sie **Funktion konvertieren**aus. Alle Aufrufe an NEXT_IDENTITY Funktion werden durch Expression (IDENT_CURRENT (Parameterwert) + IDENT_INCR (Parameterwert) ersetzt, wodurch das Verhalten der Sybase-ASE emuliert wird.  
  
-   Wenn Sie bei jedem Auftreten NEXT_IDENTITY eine Fehlermeldung ausgeben möchten, wählen Sie **mit Fehler markieren**aus. SSMA konvertiert keine Verweise auf die Funktion und markiert die Anweisung mit Fehler Kommentaren.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer/Vollmodus:** Mit Fehler markieren  
  
**PATINDEX-Funktion**  
Gibt an, ob die PATINDEX-Funktion entsprechend dem Verhalten der Sybase-ASE konvertiert wird. Der Punkt ist, dass Sybase nachfolgende Leerzeichen in einem Suchmuster schneidet. Die Problem Umgehung besteht darin, eine Umwandlung eines Wert Ausdrucks in einen Datentyp mit fester Länge mit einer maximalen Genauigkeit vorzunehmen und die RTrim-Funktion auf das Suchmuster anzuwenden.  
  
-   Um das ASE-Verhalten zu verwenden, wählen Sie **verwenden**.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Wählen Sie **nicht verwenden**aus, um das Standard-/SQL Azure Verhalten zu verwenden.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus:** Nicht verwenden  
  
**Vollständiger Modus:** Konsum  
  
**REPLICATE-Funktion**  
Die Replikations Funktion wiederholt eine Zeichenfolge so oft wie angegeben. Wenn Sie in ASE angeben, dass die Zeichenfolge NULL Mal wiederholt werden soll, ist das Ergebnis NULL. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /SQL Azure ist das Ergebnis eine leere Zeichenfolge.  
  
-   Um das ASE-Verhalten zu verwenden, wählen Sie **Funktion ersetzen**aus. Alle Aufrufe zur Replikations Funktion werden durch einen Aufruf von entweder REPLICATE_VARCHAR oder REPLICATE_NVARCHAR benutzerdefinierten Funktion basierend auf dem Typ der Parameter (erstellt in der Benutzerdatenbank mit dem Schema Namen 2SS) ersetzt, um das Verhalten der Sybase-ASE zu emulieren.  
  
-   Um das Standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -/SQL Azure Verhalten zu verwenden, wählen Sie **Funktion ersetzen**aus.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus/Vollmodus:** Replace-Funktion  
  
**Trim (LTrim, RTrim)-Funktion**  
Diese Einstellung gibt an, ob Aufrufe von Trim-Funktionen (LTrim, RTrim) durch die in der ASE entsprechenden Sybase-Syntax Funktionen ersetzt werden sollen, oder ob die aktuelle Syntax beibehalten werden soll. Die folgenden Optionen sind für diese spezielle Einstellung vorhanden:  
  
-   **Replace-Funktion**  
  
-   **Aktuelle Syntax beibehalten**  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus/Vollmodus:** Replace-Funktion  
  
**SUBSTRING-Funktion**  
In ASE gibt die Funktion `SUBSTRING(expression, start, length)` NULL zurück, wenn ein Startwert, der größer als die Anzahl der Zeichen in Expression ist, angegeben ist, oder wenn die Länge 0 (null) ist. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /SQL Azure gibt der äquivalente Ausdruck eine leere Zeichenfolge zurück.  
  
-   Um das ASE-Verhalten zu verwenden, wählen Sie **Funktion ersetzen**aus. Alle Aufrufe der SUBSTRING-Funktion werden durch einen Aufruf von SUBSTRING_VARCHAR oder SUBSTRING_NVARCHAR oder SUBSTRING_VARBINARY benutzerdefinierten Funktion basierend auf dem übergebenen Parametertyp (erstellt in der Benutzerdatenbank mit dem Schema Namen 2SS) ersetzt, um das Verhalten der Sybase-ASE zu emulieren.  
  
-   Um das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] /SQL Azure-Verhalten zu verwenden, wählen Sie **aktuelle Syntax beibehalten**aus.  
  
Wenn Sie im Feld **Modus** einen Konvertierungsmodus auswählen, wendet SSMA die folgende Einstellung an:  
  
**Standardmodus/optimistischer Modus:** Aktuelle Syntax beibehalten  
  
**Vollständiger Modus:** Replace-Funktion  
  
## <a name="tables"></a>TABLES  
**Primärschlüssel hinzufügen**  
Erstellt einen neuen Primärschlüssel in der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder-SQL Azure Tabelle, wenn eine Zugriffs Tabelle keinen Primärschlüssel oder eindeutigen Index aufweist.  
  
-   **Standardmodus**: false  
  
-   **Optimistischer Modus**: false  
  
-   **Vollständiger Modus**: true  
  
> [!NOTE]  
> Wenn eine Verbindung mit SQL Azure besteht, ist Sie standardmäßig "true".  
  
## <a name="see-also"></a>Siehe auch  
[Referenz zur Benutzeroberfläche &#40;sybasetosql&#41;](../../ssma/sybase/user-interface-reference-sybasetosql.md)  
  
