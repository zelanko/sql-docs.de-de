---
title: Projekteinstellungen (Konvertierung) (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: eeb80fa5-f530-4f21-beee-25f5a4b8ace6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 4d7f290459e1da736605acad941602399ec3ea53
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62664662"
---
# <a name="project-settings-conversion-sybasetosql"></a>Projekteinstellungen (Konvertierung) (SybaseToSQL)
Die Seite die **Projekteinstellungen** Dialogfeld enthält Einstellungen, die anpassen, wie SSMA für Sybase Adaptive Server Enterprise (ASE)-Syntax, um konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Syntax.  
  
Im Bereich für die Konvertierung finden Sie in der **Projekteinstellungen** und **Projekt Standardeinstellungen** Dialogfelder:  
  
-   Wenn Sie möchten die Einstellungen für alle SSMA-Projekten auf die **Tools** , wählen Sie im Menü **Projekt Standardeinstellungen**, klicken Sie auf **Allgemein** am unteren Rand der linken Bereich ein, und klicken Sie dann auf **Konvertierung**.  
  
-   Die Einstellungen für das aktuelle Projekt, auf die **Tools** , wählen Sie im Menü **Projekteinstellungen**, klicken Sie auf **allgemeine** am unteren Rand im linken Bereich, und klicken Sie dann auf **Konvertierung**.  
  
## <a name="miscellaneous-options"></a>Sonstige Optionen  
**@@ERROR**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure und ASE verwenden die verschiedenen Fehlercodes.  
  
Mit dieser Einstellung können Sie den Typ der Nachricht ("Warnung" oder "Fehler") angeben, die SSMA im Ausgabe- oder Fehlerliste angezeigt wird, wenn es sich um einen Verweis auf trifft **@@ERROR**  in der ASE-Code.  
  
-   Bei Auswahl von **konvertieren, und markieren Sie mit der Warnung**, SSMA konvertiert die Anweisungen und markieren Sie sie mit der Warnungskommentare.  
  
-   Bei Auswahl von **Markierung mit Fehler**, SSMA Konvertierung überspringt und markieren Sie die Anweisungen mit Fehler Kommentare.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/vollständigen-Modus:** Konvertieren Sie aus, und markieren Sie mit der Warnung  
  
**Vollmodus:** Markieren Sie mit Fehler  
  
**Konvertierung von LIKE-operator**  
Gibt an, ob wie-Operanden durch, um Übereinstimmung mit Sybase ASE-Verhalten zu konvertieren. Der Punkt ist, dass Sybase nachfolgende Leerzeichen in einem Vergleichsmuster entfernt. Die problemumgehung besteht darin, eine Umwandlung der rechte Ausdruck in einem Datentyp mit fester Länge, mit einer maximalen Genauigkeit durchführen.  
  
-   Wählen Sie **einfache Umwandlung** , die Ausdrücke ohne Korrektur zu konvertieren.  
  
-   Verwenden Sie die ASE Verhalten Select **fester Länge umgewandelt.**  
  
Wenn Sie einen Konvertierungsmodus im Modus auswählen, gilt der SSMA die folgende Einstellung:  
  
**Standard/vollständige**: Einfache Umwandlung  
  
**Vollständiger Modus**: Umwandlung in fester Länge  
  
**KONVERTIEREN SIE ODER WANDELN SIE LEERE ZEICHENFOLGEN IN NUMERISCHE TYPEN**  
Gibt an, wie leere oder leere Zeichenfolgen in CONVERT oder CAST-Ausdrücke mit numerischen Typ als Argument für Datentyp behandeln. Die folgenden Optionen sind für diese Einstellung verfügbar:  
  
-   Wählen Sie **einfache Umwandlung** , die Ausdrücke ohne Korrektur zu konvertieren.  
  
-   Wenn **leere Zeichenfolge als null numerische** ausgewählt ist, wird die Groß-/Kleinschreibung ltrim(rtrim({s})) Zeichenfolgenparameter {s} ersetzt werden bei "" klicken Sie dann 0 else {s} END-Ausdruck  
  
Wenn Sie einen Konvertierungsmodus im Modus auswählen, gilt der SSMA die folgende Einstellung:  
  
**Standard/vollständige**: Einfache Umwandlung  
  
**Vollständiger Modus**: Leere Zeichenfolge als null numerische Werte  
  
**Verkettung von NULL**  
Diese Einstellung gibt an, wie mit NULL verketten von Zeichenfolgen zu konvertieren. Die folgenden Optionen können für diese Einstellung festgelegt werden:  
  
-   **Umschließen Sie sich an ISNULL-Funktion:** Wenn diese Option festgelegt ist, wird jeder nicht Konstanten "String_expression" in Verkettung ISNULL(string_expression) eingebunden werden, und NULL-Werte mit leeren Zeichenfolge ersetzt werden.  
  
-   **Behalten der aktuellen syntax**  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/vollständigen-Modus:** Behalten der aktuellen syntax  
  
**Vollmodus:** Umschließen mit ISNULL-Funktion  
  
**Konvertierung von leeren Zeichenfolgen**  
Diese Einstellung gibt an, wie Sie leere Zeichenfolgen zu konvertieren. Die folgenden Optionen können für diese Einstellung festgelegt werden:  
  
-   **Ersetzen Sie alle Zeichenfolgenausdrücke durch Leerzeichen**  
  
-   **Ersetzen Sie leere Zeichenfolgenkonstanten mit Leerzeichen**  
  
-   Verwenden der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ select SQL Azure-Verhalten **behalten der aktuellen Syntax**.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/vollständigen-Modus:** Behalten der aktuellen syntax  
  
**Vollmodus:** Ersetzen Sie alle Zeichenfolgenausdrücke durch Leerzeichen  
  
**Konvertieren und Umwandlung binärer zeichenfolgenkonvertierung**  
Die Konvertierung der Binärwerte in Zahlen kann unterschiedliche Werte auf verschiedenen Plattformen zurück. Z. B. auf X86 Prozessoren, CONVERT (ganze Zahl, 0 x 00000100) zurückgegeben wird, 65536 in ASE und 256 in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. ASE gibt auch unterschiedliche Werte je nach Bytereihenfolge zurück.  
  
Verwenden Sie diese Einstellung zum Steuern, wie SSMA konvertiert konvertieren und die CASE-Ausdrücke, die binäre Werte enthalten:  
  
-   Wählen Sie **einfache Umwandlung** , die Ausdrücke weder Warnungen noch Korrektur zu konvertieren. Verwenden Sie diese Einstellung, wenn Sie wissen, dass die ASE-Server eine Bytereihenfolge ist, die keine Änderungen an den binären Wert erfordert.  
  
-   Wählen Sie **konvertieren, und beheben Sie** damit SSMA konvertieren, und korrigieren Sie die Ausdrücke für die Verwendung auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Die Bytereihenfolge in die literalen Konstanten wird rückgängig gemacht werden. Alle anderen binären Werte (z. B. binäre Variablen und Spalten) werden mit Fehlern gekennzeichnet. Verwenden Sie diesen Wert, wenn Sie wissen, dass der ASE-Server eine Bytereihenfolge ist, die Binärwerte Änderungen erforderlich sind.  
  
-   Wählen Sie **konvertieren, und markieren Sie mit der Warnung** haben SSMA umwandeln und korrigieren Sie die Ausdrücke, und markieren alle Ausdrücke mit Warnungskommentare konvertiert.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standardmodus:** Konvertieren Sie aus, und markieren Sie mit der Warnung  
  
**Vollständige Modus:** Einfache Umwandlung  
  
**Vollmodus:** Konvertieren und zu beheben  
  
**Dynamisches SQL**  
Verwenden Sie diese Einstellung, um den Typ der Nachricht ("Warnung" oder "Fehler") anzugeben, die SSMA im Ausgabe- oder Fehlerliste angezeigt wird, wenn es sich um dynamische SQL-Code in der ASE-Code trifft.  
  
-   Bei Auswahl von **konvertieren, und markieren Sie mit der Warnung**, SSMA dynamische SQL konvertiert und markieren Sie die Anweisungen mit Warnungskommentare.  
  
-   Bei Auswahl von **Markierung mit Fehler**, SSMA Konvertierung überspringt und markieren Sie die Anweisungen mit Fehler Kommentare.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/vollständigen-Modus:** Konvertieren Sie aus, und markieren Sie mit der Warnung  
  
**Vollmodus:** Markieren Sie mit Fehler  
  
**Konvertierung von Gleichheit überprüfen**  
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure, ist von die ANSI_NULLS-Einstellung, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure-UNKNOWN zurückgibt, wenn jede Vergleiche auf Gleichheit einen null-Wert enthält. ANSI_NULLS off festgelegt ist, Durchführung von Gleichheitsvergleichen, die null-Werte enthalten. "true" Wenn die verglichenen Spalte "und" Ausdruck "oder" zwei Ausdrücke beide sind geben null zurück. Vergleichen von Standard (ANSINULL OFF) Sybase ASE auf Gleichheit Verhalten sich wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure mit ANSI_NULLS OFF.  
  
-   Bei Auswahl von **einfache Umwandlung**, SSMA wird den ASE-Code zum Konvertieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure-Syntax ohne zusätzliche Überprüfungen für null-Werte. Verwenden Sie diese Einstellung, wenn ANSI_NULLS auf off in ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure oder überarbeiten, Durchführung von Gleichheitsvergleichen pro Fall zu Fall werden sollen.  
  
-   Bei Auswahl von **sollten Sie NULL-Werte**, SSMA wird überprüft, die null-Werte hinzufügen, indem Sie die Klauseln IS NULL und IS NOT NULL.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/vollständigen-Modus:** Einfache Umwandlung  
  
**Vollmodus:** Betrachten Sie die NULL-Werte  
  
**Formatzeichenfolgen**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure unterstützt nicht mehr die *Format_string* -Argument in Print- und RAISERROR-Anweisungen. Die *Format_string* Variable unterstützt ersetzbare Parameter direkt in der Zeichenfolge einfügen, und klicken Sie dann die Parameter zur Laufzeit zu ersetzen. Stattdessen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erfordert die vollständige Zeichenfolge mit entweder einem Zeichenfolgenliteral oder eine Zeichenfolge, die mithilfe einer Variablen erstellt. Weitere Informationen finden Sie unter der "PRINT ( [!INCLUDE[tsql](../../includes/tsql-md.md)])" Thema [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
Wenn SSMA trifft eine *Format_string* -Argument, es kann ein Zeichenfolgenliteral mit den Variablen erstellen oder eine neue Variable zu erstellen und erstellen Sie eine Zeichenfolge, indem Sie anhand dieser Variablen.  
  
-   Um ein Zeichenfolgenliteral für PRINT und RAISERROR-Funktionen verwenden möchten, wählen **neue Zeichenfolge**.  
  
    Wenn eine Print- oder RAISERROR-Anweisung keine Platzhalter und die lokale Variable verwendet, ist die Anweisung in diesem Modus kann nicht geändert. Double-Prozent-Zeichen (%) werden in Zeichenfolgenliteralen Drucken auf eine einzelne Prozentzeichen geändert werden.  
  
    Wenn eine Print- oder RAISERROR-Anweisung, Platzhalter und eine verwendet oder mehrere lokalen Variablen, wie im folgenden Beispiel:  
  
    ```  
    PRINT 'Total: %1!%%', @percent  
    ```  
    SSMA wird es in der folgenden Syntax konvertiert:  
  
    ```  
    PRINT 'Total: '+ CAST(@percent AS varchar(max)) + '%'  
    ```  
    Wenn *Format_string* ist eine Variable, z. B. in der folgenden Anweisung:  
  
    ```  
    PRINT @fmt, @arg1, @arg2  
    ```  
    SSMA eine einfache zeichenfolgenkonvertierung nicht möglich, und Sie müssen eine neue Variable zu erstellen:  
  
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
    Wenn es verwendet **neue Zeichenfolge** Modus SSMA wird vorausgesetzt, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Option CONCAT_NULL_YIELDS_NULL auf OFF festgelegt ist. SSMA wird daher nicht für null-Argumenten überprüft.  
  
-   SSMA für jede Print- und RAISERROR-Anweisung eine neue Variable zu erstellen und verwenden Sie diese Variable dann für den Zeichenfolgenwert, aktivieren **neue Variable erstellen**.  
  
    In diesem Modus Wenn eine Print- oder RAISERROR-Anweisung keine Platzhalter und die lokale Variable verwendet ersetzt SSMA alle doppelte Prozent Zeichen (%) mit einzelnen Prozent Zeichen zur Einhaltung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure-Syntax.  
  
    Wenn eine Print- oder RAISERROR-Anweisung, Platzhalter und eine verwendet oder mehrere lokalen Variablen, wie im folgenden Beispiel:  
  
    ```  
    PRINT 'Total: %1!%%', @percent  
    ```  
    SSMA wird es in der folgenden Syntax konvertiert:  
  
    ```  
    DECLARE @print_format_1 varchar(max)  
    SET @print_format_1 = 'Total: %1!%'  
    SET @print_format_1  =   
        REPLACE (@print_format_1, '%1!',   
        ISNULL(CAST (@percent AS VARCHAR(max)), ''))  
    PRINT @print_format_1  
    ```  
    Wenn *Format_string* ist eine Variable, z. B. in der folgenden Anweisung:  
  
    ```  
    PRINT @fmt, @arg1, @arg2  
    ```  
    SSMA erstellt eine neue Variable wie folgt, und null-Werte in jedem Argument überprüfen:  
  
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
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/vollständigen-Modus:** Erstellen Sie neue Zeichenfolge  
  
**Vollmodus:** Neue Variable zu erstellen  
  
**Fügen Sie einen expliziten Wert in eine Timestamp-Spalte**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure unterstützt nicht das Einfügen von expliziten Werten in Timestamp-Spalte.  
  
-   Wählen Sie zum Ausschließen von Timestamp-Spalten in INSERT-Anweisungen, **ausschließen Spalte**.  
  
-   Aktivieren, um eine Fehlermeldung an jedes Mal drucken, die eine Timestamp-Spalte in einer INSERT-Anweisung ist **Markierung mit Fehler**. In diesem Modus werden INSERT-Anweisungen werden nicht konvertiert und werden mit Fehler Kommentaren gekennzeichnet werden.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/vollständigen-Modus:** Schließen Sie Spalte  
  
**Vollmodus:** Markieren Sie mit Fehler  
  
**Temporäre Objekte, die in Prozeduren definierten Store**  
Diese Einstellung gibt an, ob die temporäre Objekte Definitionen an die in den Prozeduren angezeigt werden während der Konvertierung in den Metadaten der Datenquelle gespeichert werden sollen.  
  
-   Wählen Sie **Ja** in Metadaten zu speichern.  
  
-   Wählen Sie **keine** , wenn die Objekte nicht gespeichert werden müssen.  
  
**Standard/vollständigen-Modus:** Ja  
  
**Vollmodus:** Nein  
  
**Die tabellenkonvertierung Proxys**  
Gibt an, ob der ASE-Proxy-Tabellen konvertiert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure-Tabellen oder werden nicht konvertiert, und der Code ist mit Fehler Kommentare gekennzeichnet.  
  
-   Wählen Sie **konvertieren** Proxytabellen in reguläre Tabellen konvertieren.  
  
-   Wählen Sie **Markierung mit Fehler** um den Proxycode für die Tabelle mit Fehler Kommentaren einfach zu markieren.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/optimistische/Full-Modus:** Markieren Sie mit Fehler  
  
**RAISERROR Basis Meldungsnummer.**  
ASE-Benutzer-Nachrichten werden in jeder Datenbank gespeichert. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] benutzermeldungen werden zentral gespeichert und durch die **sys.messages** -Katalogsicht angezeigt. Darüber hinaus ASE benutzermeldungen 20000, beginnen jedoch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehlermeldungen 50001 beginnen.  
  
Diese Einstellung gibt an, die Zahl, um die Meldungsnummer des ASE-Benutzer konvertiert eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Meldung für den Benutzer. Wenn Ihre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hat benutzermeldungen in der **sys.messages** -Katalogsicht, möglicherweise müssen Sie diese Zahl auf einen höheren Wert zu ändern. Dies ist daher die konvertierte Nachricht Zahlen nicht in Konflikt mit vorhandenen Nummern sind.  
  
Beachten Sie Folgendes:  
  
-   ASE-Nachrichten im Bereich von 17000-19999 aus der Sysmessages-Systemtabelle werden und werden nicht konvertiert.  
  
-   Wenn die Nummer der Meldung, die in der RAISERROR-Anweisung verwiesen wird, eine Konstante ist, wird SSMA die Konstante, die die Nummer der neue Benutzer-Meldung zu bestimmen die Basis Meldungsnummer hinzufügen.  
  
-   Wenn die Nummer der Meldung, auf die verwiesen wird, wird eine Variable oder einen Ausdruck ist, wird SSMA eine temporäre lokale Variable erstellt.  
  
-   Im vollständigen Modus SSMA wird vorausgesetzt, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Option CONCAT_NULL_YIELDS_NULL off festgelegt ist und macht keine Überprüfungen auf null-Argumente.  
  
-   Im vollständigen Modus überprüft SSMA null-Argumente.  
  
-   RAISERROR mit ERRORDATA *Liste* wird nicht konvertiert.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/optimistische/Full-Modus:** 30001  
  
**Systemobjekte**  
Verwenden Sie diese Einstellung, den Typ der Nachricht (Warnung oder Fehler) an, die SSMA im Bereich "Ausgabe" oder "Error List" zeigt an, wenn es feststellt, dass die Verwendung der ASE-Systemobjekte.  
  
-   Bei Auswahl von **konvertieren, und markieren Sie mit der Warnung**, SSMA konvertiert Verweise auf Systemobjekte und Anweisungen mit der Warnungskommentare kennzeichnen.  
  
-   Bei Auswahl von **Markierung mit Fehler**, SSMA wird nicht konvertiert werden Verweise auf Systemobjekte und Anweisungen mit Fehler Kommentare kennzeichnen.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/vollständigen-Modus:** Konvertieren Sie aus, und markieren Sie mit der Warnung  
  
**Vollmodus:** Markieren Sie mit Fehler  
  
**Nicht aufgelöster Bezeichner**  
Verwenden Sie diese Einstellung, um den Typ der Nachricht ("Warnung" oder "Fehler") anzugeben, die SSMA im Bereich "Ausgabe" oder "Error List" zeigt an, wenn er einen Bezeichner nicht auflösen kann.  
  
-   Bei Auswahl von **konvertieren, und markieren Sie mit der Warnung**, SSMA versucht, Verweise auf nicht aufgelöste Bezeichner zu konvertieren und Anweisungen mit Warnungskommentare kennzeichnet.  
  
-   Bei Auswahl von **Markierung mit Fehler**, SSMA verweisen auf nicht aufgelöste Bezeichner nicht konvertiert und Anweisungen mit Fehler Kommentare kennzeichnen.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/vollständigen-Modus:** Konvertieren Sie aus, und markieren Sie mit der Warnung  
  
**Vollmodus:** Markieren Sie mit Fehler  
  
## <a name="system-function-options"></a>Systemoptionen-Funktion  
**CHARINDEX-Funktion**  
In App Service-Umgebung gibt CHARINDEX NULL zurück, nur, wenn alle eingegebenen Ausdrücke NULL sind. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure gibt NULL zurück, wenn jeder eingegebene Ausdruck NULL ist.  
  
-   Wählen Sie zum Verwenden der ASE-Verhalten **Replace-Funktion**. Alle Aufrufe von CHARINDEX-Funktion wird mit einem Aufruf von entweder CHARINDEX_VARCHAR oder CHARINDEX_NVARCHAR benutzerdefinierte Funktion, die basierend auf dem Typ des übergebenen Parameter (erstellt in der Benutzerdatenbank, unter dem Schema "s2ss") zum Emulieren des Verhaltens von Sybase ASE ersetzt.  
  
-   Verwenden der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ select SQL Azure-Verhalten **behalten der aktuellen Syntax**.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/vollständigen-Modus:** Behalten der aktuellen syntax  
  
**Vollmodus:** Replace-Funktion  
  
**DATALENGTH-Funktion**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] / SQL Azure und ASE unterscheiden sich den Wert, der durch die DATALENGTH-Funktion zurückgegeben wird, wenn der Wert ein Leerzeichen ist. In diesem Fall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure gibt 0 zurück und ASE gibt 1 zurück.  
  
-   Wählen Sie zum Verwenden der ASE-Verhalten **Replace-Funktion**. Alle Aufrufe an die DATALENGTH-Funktion werden durch CASE-Ausdruck zur Emulierung des Verhaltens von Sybase ASE ersetzt.  
  
-   Um den Standard- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] / select SQL Azure-Verhalten **behalten der aktuellen Syntax**.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/vollständigen-Modus:** Behalten der aktuellen syntax  
  
**Vollmodus:** Replace-Funktion  
  
**INDEX_COL-Funktion**  
ASE unterstützt ein optionales *User_id* Argument für die INDEX_COL-Funktion; allerdings [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure ist dieses Argument nicht unterstützt. Bei Verwendung der *User_id* Argument dieser Funktion kann nicht konvertiert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure-Syntax.  
  
-   Wählen Sie zum Verwenden der ASE-Verhalten **Convert-Funktion**. Wenn der Code enthält die *User_id* SSMA-Argument, wird eine Fehlermeldung angezeigt.  
  
-   Wählen Sie zum Anzeigen jedes Mal, wenn diese INDEX_COL gefunden, wird einer Fehlermeldung **Markierung mit Fehler**. SSMA wird nicht konvertiert werden Verweise auf die Funktion und kennzeichnet die Anweisung mit Fehler Kommentare.  
  
**Standard/optimistische/Full-Modus:** Markieren Sie mit Fehler  
  
**INDEX_COLORDER-Funktion**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ Eine Systemfunktion INDEX_COLORDER keinen SQL Azure.  
  
-   Wählen Sie zum Verwenden der ASE-Verhalten **Convert-Funktion**. Alle Aufrufe INDEX_COLORDER-Funktion wird durch einen Aufruf einer benutzerdefinierten Funktion mit demselben Namen INDEX_COLORDER (erstellt in der Benutzerdatenbank, unter dem Schema "s2ss"), die emuliert das Verhalten von Sybase ASE ersetzt.  
  
-   Um eine Fehlermeldung ausgegeben, jedes Mal, wenn diese INDEX_COLORDER gefunden wird, wählen Sie **Markierung mit Fehler**. SSMA wird nicht konvertiert werden Verweise auf die Funktion und kennzeichnet die Anweisung mit Fehler Kommentare.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/optimistische/Full-Modus:** Markieren Sie mit Fehler  
  
**Left- und RIGHT-Funktionen**  
Links und rechts-Funktionen in Sybase Verhalten sich anders für negative Length-Parameter.  
  
-   Wählen Sie zum Verwenden der ASE-Verhalten **Replace-Funktion**. Der Length-Parameter wird durch die CASE-Ausdruck ersetzt die für den negativen Wert null zurückgeben würde.  
  
-   Wählen Sie zum Verwenden der SQL Server-Verhalten **behalten der aktuellen Syntax**  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/vollständigen-Modus:** Behalten der aktuellen syntax  
  
**Vollmodus:** Replace-Funktion  
  
> [!NOTE]  
> Wenn der Length-Parameter einen Literalwert und nicht auf einen komplexen Ausdruck ist, wird der Längenwert immer mit Null, unabhängig von der projekteinstellung ersetzt.  
  
**NEXT_IDENTITY-Funktion**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ Eine Systemfunktion NEXT_IDENTITY keinen SQL Azure.  
  
-   Wählen Sie zum Verwenden der ASE-Verhalten **Convert-Funktion**. Alle Aufrufe NEXT_IDENTITY-Funktion wird ersetzt, mit dem Ausdruck (IDENT_CURRENT(parameter Value) + IDENT_INCR(parameter Value) die emuliert das Verhalten von Sybase ASE.  
  
-   Um eine Fehlermeldung ausgegeben, jedes Mal, wenn diese NEXT_IDENTITY gefunden wird, wählen Sie **Markierung mit Fehler**. SSMA wird nicht konvertiert werden Verweise auf die Funktion und kennzeichnet die Anweisung mit Fehler Kommentare.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/optimistische/Full-Modus:** Markieren Sie mit Fehler  
  
**PATINDEX-Funktion**  
Gibt an, ob PATINDEX-Funktion, um Übereinstimmung mit Sybase ASE-Verhalten zu konvertieren. Der Punkt ist, dass Sybase nachfolgende Leerzeichen in ein Suchmuster werden entfernt. Die problemumgehung besteht eine Umwandlung des Value-Ausdruck mit einer festen Länge, die Daten mit einer maximalen Genauigkeit geben und Anwenden von Rtrim-Funktion, um Muster zu suchen.  
  
-   Verwenden Sie die ASE Verhalten Select **verwenden**.  
  
-   Um den Standard- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ select SQL Azure-Verhalten **verwenden Sie keine**.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/vollständigen-Modus:** Nicht verwenden  
  
**Vollmodus:** Verwenden Sie  
  
**REPLICATE-Funktion**  
Die REPLICATE-Funktion wird eine Zeichenfolge die angegebene Anzahl von Malen wiederholt. Wenn Sie angeben, dass die Zeichenfolge null Mal wiederholt, ist das Ergebnis in App Service-Umgebung null. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure, das Ergebnis ist eine leere Zeichenfolge.  
  
-   Wählen Sie zum Verwenden der ASE-Verhalten **Replace-Funktion**. Alle Aufrufe von REPLICATE-Funktion wird mit einem Aufruf von entweder REPLICATE_VARCHAR oder REPLICATE_NVARCHAR benutzerdefinierte Funktion, die basierend auf dem Typ des übergebenen Parameter (erstellt in der Benutzerdatenbank, unter dem Schema "s2ss") zum Emulieren des Verhaltens von Sybase ASE ersetzt.  
  
-   Verwenden Sie die Standardeinstellung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ select SQL Azure-Verhalten **Replace-Funktion**.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/optimistische Modus/Full-Modus:** Replace-Funktion  
  
**TRIM (LTRIM, RTRIM)-Funktion**  
Diese Einstellung gibt an, ob Aufrufe von Trim (LTRIM, RTRIM)-Funktionen durch die Syntax der Funktionen von Sybase ASE-äquivalent zu ersetzen oder Syntax für die aktuelle beibehalten. Die folgenden Optionen sind für diese Einstellung vorhanden:  
  
-   **Replace-Funktion**  
  
-   **Behalten der aktuellen syntax**  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/optimistische Modus/Full-Modus:** Replace-Funktion  
  
**SUBSTRING-Funktion**  
In App Service-Umgebung die Funktion `SUBSTRING(expression, start, length)` gibt NULL zurück, wenn ein Start-Wert, der größer als die Anzahl der Zeichen im Ausdruck angegeben wird oder wenn die Länge 0 (null) entspricht. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/ SQL Azure, der entsprechende Ausdruck eine leere Zeichenfolge zurückgegeben.  
  
-   Wählen Sie zum Verwenden der ASE-Verhalten **Replace-Funktion**. Alle Aufrufe an die SUBSTRING-Funktion wird durch einen Aufruf basierend auf dem Typ von Parametern übergeben (erstellt in der Benutzerdatenbank, unter dem Schemanamen "s2ss") zum emulieren SUBSTRING_VARCHAR oder SUBSTRING_NVARCHAR oder SUBSTRING_VARBINARY eine benutzerdefinierte Funktion ersetzt die Sybase ASE-Verhalten.  
  
-   Verwenden der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] / select SQL Azure-Verhalten **behalten der aktuellen Syntax**.  
  
Bei Auswahl einer Konvertierungsmodus, in der **Modus** SSMA Feld gilt die folgende Einstellung:  
  
**Standard/vollständigen-Modus:** Behalten der aktuellen syntax  
  
**Vollmodus:** Replace-Funktion  
  
## <a name="tables"></a>TABLES  
**Fügen Sie Primärschlüssel**  
Erstellt einen neuen primären Schlüssel in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Tabelle, wenn eine Access-Tabelle ohne Primärschlüssel oder eindeutigen Index verfügt.  
  
-   **Im Modus Standard**: False  
  
-   **Vollständige**: False  
  
-   **Vollständiger Modus**: Wahr  
  
> [!NOTE]  
> Beim Verbinden mit SQL Azure, ist es standardmäßig "true".  
  
## <a name="see-also"></a>Siehe auch  
[Referenz zur Benutzeroberfläche &#40;SybaseToSQL&#41;](../../ssma/sybase/user-interface-reference-sybasetosql.md)  
  
