---
title: Konvertieren von Oracle-Schemas (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Conversion Results
ms.assetid: e021182d-31da-443d-b110-937f5db27272
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 18da150a435b5d3d61740139309d109a16691da3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63288891"
---
# <a name="converting-oracle-schemas-oracletosql"></a>Konvertieren von Oracle-Schemas (OracleToSQL)
Nachdem Sie mit Oracle verbunden haben, verbunden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und das Projekt festlegen und Optionen für die Zuordnung von Daten, können Sie Oracle-Datenbank-Objekte zu konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankobjekten.  
  
## <a name="the-conversion-process"></a>Konvertierungsprozess  
Nimmt die Objektdefinitionen von Oracle, konvertiert diese in ähnlichen konvertieren Datenbankobjekten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objekte und lädt dann diese Informationen in der SSMA-Metadaten. Er lädt nicht die Informationen in die Instanz der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können dann die Objekte und deren Eigenschaften anzeigen, mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer.  
  
Bei der Konvertierung gibt SSMA Ausgabe in den Bereich Ausgabe und Fehlermeldungen in den Bereich Fehlerliste angezeigt. Verwenden Sie die Ausgabe- und Informationen, um festzustellen, ob Sie so ändern Sie Ihre Oracle-Datenbanken oder den Konvertierungsprozess Ihrer, um die gewünschte Konvertierungsergebnisse erhalten haben.  
  
## <a name="setting-conversion-options"></a>Festlegen von Optionen  
Lesen Sie vor dem Konvertieren von Objekten, die die Projektoptionen für die Konvertierung in den **Projekteinstellungen** Dialogfeld. Verwenden Sie das Dialogfeld zu öffnen, können Sie festlegen, wie der SSMA-Funktionen und globale Variablen konvertiert. Weitere Informationen finden Sie unter [Projekteinstellungen &#40;Konvertierung&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md).  
  
## <a name="conversion-results"></a>Konvertierungsergebnisse  
Die folgende Tabelle zeigt, welche Oracle Objekte konvertiert werden, und der daraus resultierende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte:  
  
|||  
|-|-|  
|Oracle-Objekte|Resultierende SQL Server-Objekte|  
|Funktionen|Wenn die Funktion direkt kann, um konvertiert werden [!INCLUDE[tsql](../../includes/tsql-md.md)], SSMA wird eine Funktion erstellt.<br /><br />In einigen Fällen muss die Funktion an eine gespeicherte Prozedur konvertiert werden. In diesem Fall erstellt SSMA an eine gespeicherte Prozedur und eine Funktion, die gespeicherte Prozedur aufruft.|  
|Vorgehensweisen|Wenn die Prozedur direkt kann, um konvertiert werden [!INCLUDE[tsql](../../includes/tsql-md.md)], SSMA erstellt eine gespeicherte Prozedur.<br /><br />In einigen Fällen muss eine gespeicherte Prozedur in einer autonomen Transaktion aufgerufen werden. In diesem Fall SSMA zwei gespeicherte Prozeduren erstellt: eine, die implementiert werden, die Prozedur, und eine andere, die zum Aufrufen der Implementierung verwendet wird, gespeicherte Prozedur.|  
|Pakete|SSMA erstellt einen Satz von gespeicherten Prozeduren und Funktionen, die von ähnlichen Objektnamen vereinheitlicht sind.|  
|Sequenzen|SSMA erstellt Sequenzobjekte (SQL Server 2012 oder SQL Server 2014) oder Oracle-Sequenzen emuliert.|  
|Tabellen mit abhängigen Objekten wie Indizes und Trigger|SSMA erstellt Tabellen mit abhängigen Objekten.|  
|Abhängige Objekte, z. B. Trigger anzeigen|SSMA erstellt Ansichten mit abhängigen Objekten.|  
|Materialisierte Sichten|**SSMA erstellt indizierte Sichten in SQLServer bis auf einige Ausnahmen. Konvertierung schlägt fehl, wenn die materialisierte Sicht eine oder mehrere der folgenden Konstrukte enthält:**<br /><br />Benutzerdefinierte Funktion<br /><br />Nicht deterministische Feld / Funktion / Ausdruck ein, wählen Sie im, in dem oder der GROUP BY-Klauseln<br /><br />Verwendung von "float"-Spalte in SELECT *, wobei oder GROUP BY-Klauseln (Sonderfall des vorherigen Problem)<br /><br />Benutzerdefinierter Datentyp (inkl. geschachtelten Tabellen)<br /><br />COUNT (distinct &lt;Feld&gt;)<br /><br />FETCH<br /><br />OUTER-Joins (LEFT, RIGHT oder FULL)<br /><br />Unterabfrage, die andere anzeigen<br /><br />ÜBER, RANK, LEAD, MELDEN SIE SICH<br /><br />MIN, MAX<br /><br />UNION, MINUS, INTERSECT<br /><br />HAVING|  
|Trigger|**SSMA erstellt Trigger basierend auf den folgenden Regeln:**<br /><br />Bevor Trigger INSTEAD OF-Trigger in konvertiert wurden.<br /><br />AFTER-Trigger werden in AFTER-Trigger konvertiert.<br /><br />INSTEAD OF-Trigger werden in INSTEAD OF-Trigger konvertiert. Mehrere für den gleichen Vorgang definierten INSTEAD OF-Trigger werden in einem Trigger kombiniert.<br /><br />Trigger auf Zeilenebene werden emuliert Verwenden von Cursorn.<br /><br />Kaskadierende Trigger werden in mehrere einzelne Trigger konvertiert.|  
|Synonyme|**Synonyme werden für die folgenden Objekttypen erstellt:**<br /><br />Tabellen und Objekttabellen<br /><br />Ansichten und Objekt-Ansichten<br /><br />Gespeicherte Prozeduren<br /><br />Funktionen<br /><br />**Synonyme für die folgenden Objekte werden aufgelöst und durch direkte Objektverweise ersetzt:**<br /><br />Sequenzen<br /><br />Pakete<br /><br />Schemaobjekte für Java-Klasse<br /><br />Benutzerdefinierte Objekttypen<br /><br />Synonyme für ein anderes Synonym können nicht migriert werden und werden als Fehler gekennzeichnet werden.<br /><br />Synonyme sind nicht für Materialized Ansichten erstellt.|  
|Benutzerdefinierte Typen|**SSMA bietet keine Unterstützung für die Konvertierung von benutzerdefinierten Typen. Benutzerdefinierte Typen, einschließlich der Verwendung in PL/SQL-Programmen sind mit speziellen Konvertierungsfehler, die durch MDX die folgenden Regeln gekennzeichnet:**<br /><br />In varchar(8000)-Werte konvertiert, wird die Tabellenspalte, der einen benutzerdefinierten Typ konvertiert.<br /><br />Argument vom Benutzer definierten Typ an eine gespeicherte Prozedur oder Funktion in varchar(8000)-Werte konvertiert, konvertiert wird.<br /><br />Variablen des benutzerdefinierten Typs in PL/SQL-Block wird in varchar(8000)-Werte konvertiert, konvertiert.<br /><br />Tabelle der Objekte wird in eine Standardtabelle konvertiert.<br /><br />Anzeigen des Objekts wird in einer Standardsicht konvertiert.|  
  
## <a name="converting-oracle-database-objects"></a>Konvertieren von Oracle-Datenbank-Objekten  
Um Oracle-Datenbank-Objekte zu konvertieren, wählen Sie zuerst die Objekte, die Sie konvertieren möchten, und müssen dann SSMA, die die Konvertierung nicht ausgeführt. Anzeigen von ausgehenden Nachrichten bei der Konvertierung auf den **Ansicht** , wählen Sie im Menü **Ausgabe**.  
  
**So konvertieren Sie Oracle-Objekte in SQL Server-syntax**  
  
1.  Klicken Sie in Oracle-Metadaten-Explorer, erweitern Sie den Oracle-Server, und erweitern Sie dann **Schemas**.  
  
2.  Wählen Sie Objekte zu konvertieren:  
  
    -   Um alle Schemas zu konvertieren, wählen Sie das Kontrollkästchen neben **Schemas**.  
  
    -   Zum konvertieren, oder lassen Sie eine Datenbank, wählen Sie das Kontrollkästchen neben dem Schemanamen.  
  
    -   Konvertieren, oder lassen Sie eine Kategorie von Objekten, erweitern Sie ein Schema, und aktivieren Sie oder deaktivieren Sie das Kontrollkästchen neben der Kategorie.  
  
    -   Konvertieren, oder lassen Sie einzelne Objekte, erweitern Sie die Kategorieordner, und aktivieren Sie oder deaktivieren Sie das Kontrollkästchen neben dem Objekt.  
  
3.  Um alle ausgewählten Objekte zu konvertieren, Maustaste **Schemas** , und wählen Sie **Schema konvertieren**.  
  
    Sie können auch einzelne Objekte oder Kategorien von Objekten von der rechten Maustaste auf das Objekt oder der übergeordnete Ordner, und wählen Sie dann konvertieren **Schema konvertieren**.  
  
## <a name="viewing-conversion-problems"></a>Probleme bei der Konvertierung anzeigen  
Einige Oracle-Objekte können nicht konvertiert werden. Sie können die Abschlussraten für den Erfolg bestimmen, durch Anzeigen der Zusammenfassung Konvertierungsbericht.  
  
**Zum Anzeigen eines Übersichtsberichts**  
  
1.  Wählen Sie in der Oracle-Metadaten-Explorer, **Schemas**.  
  
2.  Wählen Sie im rechten Bereich die **Bericht** Registerkarte.  
  
    Dieser Bericht zeigt die Zusammenfassung Bewertungsbericht für alle Datenbankobjekte, die bewertet oder konvertiert wurden. Sie können auch einen Zusammenfassungsbericht für einzelne Objekte anzeigen:  
  
    -   Um den Bericht für ein einzelnes Schema anzuzeigen, wählen Sie das Schema in der Oracle-Metadaten-Explorer aus.  
  
    -   Um den Bericht für ein einzelnes Objekt anzuzeigen, wählen Sie das Objekt in der Oracle-Metadaten-Explorer aus. Objekten, die Probleme bei der Konvertierung zu haben, ist ein rotes Fehlersymbol.  
  
Für Objekte, die Konvertierung fehlgeschlagen ist, können Sie die Syntax anzeigen, die die Konvertierungsfehler bewirkt, dass geführt haben.  
  
**Probleme beim Konvertieren der einzelnen anzeigen**  
  
1.  Erweitern Sie in der Oracle-Metadaten-Explorer, **Schemas**.  
  
2.  Erweitern Sie das Schema, das ein rotes Fehlersymbol zeigt.  
  
3.  Erweitern Sie einen Ordner mit einem roten Fehlersymbol, unter dem Schema.  
  
4.  Wählen Sie das Objekt mit einem roten Fehlersymbol.  
  
5.  Klicken Sie im rechten Bereich auf die **Bericht** Registerkarte.  
  
6.  Am oberen Rand der **Bericht** Registerkarte wird eine Dropdown-Liste. Wenn die Liste zeigt **Statistiken**, ändern Sie die Auswahl auf **Quelle**.  
  
    SSMA wird der Quellcode und verschiedene Schaltflächen direkt über dem Code angezeigt.  
  
7.  Klicken Sie auf die **nächsten Problem** Schaltfläche. Dies ist ein rotes Fehlersymbol mit einem Pfeil nach rechts.  
  
    SSMA wird es sich um den ersten problematisch Quellcode hervorheben, die, den Sie in das aktuelle Objekt findet.  
  
Für jedes Element, das nicht konvertiert werden konnten, müssen Sie bestimmen, was Sie mit diesem Objekt tun möchten:  
  
-   Sie können den Quellcode für die Prozeduren auf die **SQL** Registerkarte.  
  
-   Sie können ändern, dass das Objekt in der Oracle-Datenbank zu entfernen oder die problematischen Code zu überarbeiten. Um den aktualisierten Code in SSMA laden zu können, müssen Sie die Metadaten zu aktualisieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Oracle-Datenbank &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md).  
  
-   Sie können das Objekt von der Migration ausschließen. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer und Oracle-Metadaten-Explorer, deaktivieren Sie das Kontrollkästchen neben dem Element vor dem Laden der Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Migrieren von Daten von Oracle.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrationsvorgangs besteht darin [Laden Sie die konvertierte Objekte in SQL Server](loading-converted-database-objects-into-sql-server-oracletosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Oracle zu SQLServer-Datenbanken &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
