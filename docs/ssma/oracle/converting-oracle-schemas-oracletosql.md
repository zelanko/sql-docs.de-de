---
title: Umstellen von Oracle-Schemas (oracleto SQL) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Oracle-Datenbankobjekte in SQL Server Datenbankobjekte mit SSMA für Oracle konvertieren, nachdem Sie Optionen festgelegt und eine Verbindung mit Oracle und SQL Server hergestellt haben.
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
manager: shamikg
ms.openlocfilehash: 5eaf0970f5bc7d3aef49e83906a32295e9138cd9
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293577"
---
# <a name="converting-oracle-schemas-oracletosql"></a>Konvertieren von Oracle-Schemas (OracleToSQL)
Nachdem Sie eine Verbindung mit Oracle hergestellt, eine Verbindung mit hergestellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Projekt-und Daten Zuordnungsoptionen festgelegt haben, können Sie Oracle-Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbankobjekte konvertieren.  
  
## <a name="the-conversion-process"></a>Der Konvertierungsprozess  
Das Konvertieren von Datenbankobjekten übernimmt die Objekt Definitionen aus Oracle, konvertiert sie in ähnliche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte und lädt diese Informationen dann in die SSMA-Metadaten. Die Informationen werden nicht in die Instanz von geladen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Anschließend können Sie die Objekte und deren Eigenschaften mit dem Metadaten- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorer anzeigen.  
  
Während der Konvertierung druckt SSMA Ausgabemeldungen im Ausgabebereich und Fehlermeldungen in den Fehlerliste Bereich. Bestimmen Sie anhand der Ausgabe-und Fehlerinformationen, ob Sie Ihre Oracle-Datenbanken oder den Konvertierungsprozess ändern müssen, um die gewünschten Konvertierungs Ergebnisse zu erhalten.  
  
## <a name="setting-conversion-options"></a>Festlegen von Konvertierungsoptionen  
Überprüfen Sie vor dem Konvertieren von Objekten die Projekt Konvertierungsoptionen im Dialogfeld **Projekteinstellungen** . Mit diesem Dialogfeld können Sie festlegen, wie SSMA Funktionen und globale Variablen konvertiert. Weitere Informationen finden Sie unter [Project Settings &#40;Conversion&#41; &#40;oracleto SQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md).  
  
## <a name="conversion-results"></a>Konvertierungs Ergebnisse  
Die folgende Tabelle zeigt, welche Oracle-Objekte konvertiert werden, und die resultierenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte:  
  
|||  
|-|-|  
|Oracle-Objekte|Resultierende SQL Server Objekte|  
|Functions|Wenn die Funktion direkt in konvertiert werden kann [!INCLUDE[tsql](../../includes/tsql-md.md)] , erstellt SSMA eine Funktion.<br /><br />In einigen Fällen muss die Funktion in eine gespeicherte Prozedur konvertiert werden. In diesem Fall erstellt SSMA eine gespeicherte Prozedur und eine Funktion, die die gespeicherte Prozedur aufruft.|  
|Prozeduren|Wenn die Prozedur direkt in konvertiert werden kann [!INCLUDE[tsql](../../includes/tsql-md.md)] , erstellt SSMA eine gespeicherte Prozedur.<br /><br />In einigen Fällen muss eine gespeicherte Prozedur in einer autonomen Transaktion aufgerufen werden. In diesem Fall erstellt SSMA zwei gespeicherte Prozeduren: einen, der die Prozedur implementiert, und einen weiteren, der zum Aufrufen der implementierenden gespeicherten Prozedur verwendet wird.|  
|Pakete|SSMA erstellt einen Satz gespeicherter Prozeduren und Funktionen, die durch ähnliche Objektnamen vereinheitlicht werden.|  
|Sequenzen|SSMA erstellt Sequenz Objekte (SQL Server 2012 oder SQL Server 2014) oder emuliert Oracle-Sequenzen.|  
|Tabellen mit abhängigen Objekten, z. b. Indizes und Trigger|SSMA erstellt Tabellen mit abhängigen Objekten.|  
|Anzeigen mit abhängigen Objekten, z. b. Triggern|SSMA erstellt Sichten mit abhängigen Objekten.|  
|Materialisierte Sichten|**SSMA erstellt indizierte Sichten auf SQL Server mit einigen Ausnahmen. Bei der Konvertierung tritt ein Fehler auf, wenn die materialisierte Sicht mindestens eines der folgenden Konstrukte umfasst:**<br /><br />Benutzerdefinierte Funktion<br /><br />Nicht deterministisches Feld/Funktion/Ausdruck in SELECT-, WHERE-oder GROUP BY-Klauseln<br /><br />Verwendung der float-Spalte in SELECT *-, WHERE-oder GROUP BY-Klauseln (Sonderfall des vorherigen Problems)<br /><br />Benutzerdefinierter Datentyp (einschließlich der Tabellen)<br /><br />COUNT (eindeutiges &lt; Feld &gt; )<br /><br />FETCH<br /><br />OUTER-Joins (LEFT, RIGHT oder FULL)<br /><br />Unterabfrage, andere Ansicht<br /><br />Over, Rank, Lead, Log<br /><br />MIN, MAX<br /><br />Union, minus, Intersect<br /><br />HAVING|  
|Trigger|**SSMA erstellt Trigger auf der Grundlage der folgenden Regeln:**<br /><br />Bevor Trigger in anstelle von Triggern konvertiert werden.<br /><br />AFTER-Trigger werden in After-Trigger konvertiert.<br /><br />Anstelle von Triggern werden in anstelle von Triggern konvertiert. Mehrere anstelle von Triggern, die für denselben Vorgang definiert sind, werden zu einem Trigger kombiniert.<br /><br />Trigger auf Zeilenebene werden mithilfe von Cursorn emuliert.<br /><br />Kaskadierende Trigger werden in mehrere einzelne Trigger konvertiert.|  
|Synonyme|**Synonyme werden für die folgenden Objekttypen erstellt:**<br /><br />Tabellen und Objekt Tabellen<br /><br />Sichten und Objekt Sichten<br /><br />Gespeicherte Prozeduren<br /><br />Functions<br /><br />**Synonyme für die folgenden Objekte werden aufgelöst und durch direkte Objekt Verweise ersetzt:**<br /><br />Sequenzen<br /><br />Pakete<br /><br />Java-Klassen Schema Objekte<br /><br />Benutzerdefinierte Objekttypen<br /><br />Synonyme für ein anderes Synonym können nicht migriert werden und werden als Fehler markiert.<br /><br />Synonyme werden für materialisierte Sichten nicht erstellt.|  
|Benutzerdefinierte Typen|**SSMA bietet keine Unterstützung für die Konvertierung von benutzerdefinierten Typen. Benutzerdefinierte Typen, einschließlich der Verwendung in PL/SQL-Programmen, werden mit speziellen Konvertierungs Fehlern gekennzeichnet, die durch die folgenden Regeln gesteuert werden:**<br /><br />Die Tabellenspalte eines benutzerdefinierten Typs wird in varchar (8000) konvertiert.<br /><br />Das Argument des benutzerdefinierten Typs einer gespeicherten Prozedur oder Funktion wird in varchar (8000) konvertiert.<br /><br />Die Variable des benutzerdefinierten Typs im PL/SQL-Block wird in varchar (8000) konvertiert.<br /><br />Die Objekttabelle wird in eine Standard Tabelle konvertiert.<br /><br />Die Objekt Ansicht wird in eine Standard Ansicht konvertiert.|  
  
## <a name="converting-oracle-database-objects"></a>Oracle Database Objekte werden umgerechnet  
Zum Konvertieren von Oracle-Datenbankobjekten wählen Sie zunächst die Objekte aus, die Sie konvertieren möchten, und lassen die Konvertierung von SSMA durchführen. Wenn Sie während der Konvertierung Ausgabemeldungen anzeigen möchten, wählen Sie im Menü **Ansicht** die Option **Ausgabe**aus.  
  
**So konvertieren Sie Oracle-Objekte in SQL Server Syntax**  
  
1.  Erweitern Sie im Oracle-metadatenexplorer den Oracle-Server, und erweitern Sie dann **Schemas**.  
  
2.  Zu konvertierende Objekte auswählen:  
  
    -   Aktivieren Sie das Kontrollkästchen neben **Schemas**, um alle Schemas zu konvertieren.  
  
    -   Aktivieren Sie das Kontrollkästchen neben dem Schema Namen, um eine Datenbank zu konvertieren oder auszulassen.  
  
    -   Wenn Sie eine Kategorie von Objekten konvertieren oder weglassen möchten, erweitern Sie ein Schema, und aktivieren bzw. deaktivieren Sie das Kontrollkästchen neben der Kategorie.  
  
    -   Wenn Sie einzelne Objekte konvertieren oder weglassen möchten, erweitern Sie den Ordner Category, und aktivieren oder deaktivieren Sie das Kontrollkästchen neben dem Objekt.  
  
3.  Um alle ausgewählten Objekte zu konvertieren, klicken Sie mit der rechten Maustaste auf **Schemas** , und wählen Sie **Schema konvertieren**.  
  
    Sie können auch einzelne Objekte oder Kategorien von Objekten konvertieren, indem Sie mit der rechten Maustaste auf das Objekt oder seinen übergeordneten Ordner klicken und dann **Schema konvertieren**auswählen.  
  
## <a name="viewing-conversion-problems"></a>Anzeigen von Konvertierungs Problemen  
Einige Oracle-Objekte werden möglicherweise nicht konvertiert. Sie können die Erfolgsraten der Konvertierung ermitteln, indem Sie den Zusammenfassungs Bericht für die Zusammenfassung anzeigen  
  
**So zeigen Sie einen Zusammenfassungs Bericht an**  
  
1.  Wählen Sie im Oracle-metadatenexplorer **Schemas**aus.  
  
2.  Wählen Sie im rechten Bereich die Registerkarte **Bericht** aus.  
  
    Dieser Bericht zeigt den Zusammenfassungs Bewertungsbericht für alle Datenbankobjekte an, die bewertet oder konvertiert wurden. Sie können auch einen Zusammenfassungs Bericht für einzelne Objekte anzeigen:  
  
    -   Um den Bericht für ein einzelnes Schema anzuzeigen, wählen Sie das Schema im Oracle-metadatenexplorer aus.  
  
    -   Um den Bericht für ein einzelnes Objekt anzuzeigen, wählen Sie das Objekt im Oracle-metadatenexplorer aus. Bei Objekten, die Konvertierungsprobleme aufweisen, wird ein rotes Fehler Symbol angezeigt.  
  
Bei Objekten, die nicht erfolgreich konvertiert werden konnten, können Sie die Syntax anzeigen, die zu einem Konvertierungs Fehler geführt hat.  
  
**So zeigen Sie einzelne Konvertierungsprobleme an**  
  
1.  Erweitern Sie in Oracle Metadata Explorer den Eintrag **Schemas**.  
  
2.  Erweitern Sie das Schema, das ein rotes Fehler Symbol anzeigt.  
  
3.  Erweitern Sie unter dem Schema einen Ordner mit einem roten Fehler Symbol.  
  
4.  Wählen Sie das Objekt mit einem roten Fehler Symbol aus.  
  
5.  Klicken Sie im rechten Bereich auf die Registerkarte **Bericht** .  
  
6.  Am oberen Rand der Registerkarte **Bericht** befindet sich eine Dropdown Liste. Wenn in der Liste **Statistiken**angezeigt werden, ändern Sie die Auswahl in **Quelle**.  
  
    SSMA zeigt den Quellcode und mehrere Schaltflächen direkt oberhalb des Codes an.  
  
7.  Klicken Sie auf die Schaltfläche **nächstes Problem** . Dabei handelt es sich um ein rotes Fehler Symbol mit einem Pfeil, der nach rechts zeigt.  
  
    SSMA hebt den ersten problematischen Quell Code hervor, der im aktuellen-Objekt gefunden wird.  
  
Sie müssen für jedes Element, das nicht konvertiert werden konnte, bestimmen, was Sie mit diesem Objekt tun möchten:  
  
-   Sie können den Quellcode für Prozeduren auf der Registerkarte " **SQL** " ändern.  
  
-   Sie können das Objekt in der Oracle-Datenbank ändern, um problematischen Code zu entfernen oder zu überarbeiten. Um den aktualisierten Code in SSMA zu laden, müssen Sie die Metadaten aktualisieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Oracle Database &#40;oracleto SQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md).  
  
-   Sie können das Objekt von der Migration ausschließen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Deaktivieren Sie im metadatenexplorer und im Oracle-metadatenexplorer das Kontrollkästchen neben dem Element, bevor Sie die Objekte in Laden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Daten aus Oracle migrieren.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrations Vorgangs besteht darin, [die konvertierten Objekte in SQL Server zu laden](loading-converted-database-objects-into-sql-server-oracletosql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von Oracle-Datenbanken zu SQL Server &#40;oracleto SQL-&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
