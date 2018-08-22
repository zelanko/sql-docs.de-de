---
title: Konvertieren von MySQL-Datenbanken (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ac21850b-fb32-4704-9985-5759b7c688c7
caps.latest.revision: 17
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 83cd35918c6d2fbc3190ebcedd3606b622e549f1
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393190"
---
# <a name="converting-mysql-databases-mysqltosql"></a>Konvertieren von MySQL-Datenbanken (MySqlToSql)
Nachdem Sie eine Verbindung mit MySQL hergestellt haben, verbunden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, und Set-Projekt und Optionen für die Zuordnung von Daten, können Sie MySQL-Datenbank-Objekten, konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbankobjekte.  
  
## <a name="the-conversion-process"></a>Konvertierungsprozess  
Die Objektdefinitionen aus MySQL akzeptiert, konvertiert diese in ähnliche konvertieren Datenbankobjekten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Objekte, und lädt dann diese Informationen in der SSMA-Metadaten. Er lädt nicht die Informationen in die Instanz der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können dann die Objekte und deren Eigenschaften anzeigen, mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer.  
  
Bei der Konvertierung gibt SSMA Ausgabe in den Bereich Ausgabe und Fehlermeldungen in den Bereich Fehlerliste angezeigt. Verwenden Sie die Ausgabe- und Informationen, um festzustellen, ob Sie so ändern Sie Ihre MySQL-Datenbanken oder den Konvertierungsprozess Ihrer, um die gewünschte Konvertierungsergebnisse erhalten haben.  
  
## <a name="setting-conversion-options"></a>Festlegen von Optionen  
Lesen Sie vor dem Konvertieren von Objekten, die die Projektoptionen für die Konvertierung in den **Projekteinstellungen** Dialogfeld. Verwenden Sie das Dialogfeld zu öffnen, können Sie festlegen, wie Tabellen und Indizes durch SSMA konvertiert. Weitere Informationen finden Sie unter [Projekteinstellungen &#40;Konvertierung&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
  
## <a name="conversion-results"></a>Konvertierungsergebnisse  
Die folgende Tabelle zeigt, welche MySQL Objekte konvertiert werden, und das resultierende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte:  
  
|||  
|-|-|  
|**MySQL-Objekten**|**Resultierende SQL Server-Objekte**|  
|Tabellen mit abhängigen Objekte wie Indizes|SSMA erstellt Tabellen mit abhängigen Objekten. Tabelle wird mit allen Indizes und Einschränkungen konvertiert. Indizes werden in Separate konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte.<br /><br />**Zuordnen von räumlichen Datentypen** kann nur auf Tabellenebene für die Knoten ausgeführt werden.<br /><br />Weitere Informationen zu den Einstellungen für die Konvertierung der Tabelle finden Sie unter [Konvertierungseinstellungen](conversion-settings-mysqltosql.md)|  
|Funktionen|Wenn die Funktion direkt in Transact-SQL konvertiert werden kann, wird eine Funktion von SSMA erstellt. In einigen Fällen muss die Funktion an eine gespeicherte Prozedur konvertiert werden. Dies kann erfolgen mithilfe von **Funktion Konvertierung** in den Projekteinstellungen. In diesem Fall erstellt SSMA an eine gespeicherte Prozedur und eine Funktion, die gespeicherte Prozedur aufruft.<br /><br />**Optionen, die angegeben werden:**<br /><br />Konvertieren Sie gemäß den projekteinstellungen<br /><br />Konvertieren in Funktion<br /><br />Konvertieren Sie in der gespeicherten Prozedur<br /><br />Weitere Informationen zu Einstellungen für die Konvertierung von Funktion, finden Sie unter [Konvertierungseinstellungen](conversion-settings-mysqltosql.md)|  
|Vorgehensweisen|Wenn die Prozedur direkt in Transact-SQL konvertiert werden kann, wird in SSMA eine gespeicherte Prozedur erstellt. In einigen Fällen muss eine gespeicherte Prozedur in einer autonomen Transaktion aufgerufen werden. In diesem Fall SSMA zwei gespeicherte Prozeduren erstellt: eine, die implementiert werden, die Prozedur, und eine andere, die zum Aufrufen der Implementierung verwendet wird, gespeicherte Prozedur.|  
|Datenbankkonvertierung|Datenbanken als MySQL-Objekte werden nicht direkt von SSMA für MySQL konvertiert. MySQL-Datenbanken mehr wie einen Schemanamen behandelt, und alle physischen Parameter sind während der Konvertierung verloren gehen. SSMA für MySQL verwendet [Zuordnen von MySQL-Datenbanken in SQL Server-Schemas &#40;MySQLToSQL&#41; ](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md) Objekte von MySQL-Datenbank auf der entsprechenden SQL Server-Datenbank/Schema-Paar zugeordnet.|  
|Trigger-Konvertierung|**SSMA erstellt Trigger basierend auf den folgenden Regeln:**<br /><br />Vor dem Trigger in INSTEAD OF-T-SQL-Trigger konvertiert werden<br /><br />AFTER-Trigger werden in der nach dem T-SQL-Trigger mit oder ohne Iterationen pro Zeilen konvertiert.|  
|Ansicht-Konvertierung|SSMA erstellt Ansichten mit abhängigen Objekten|  
|-Anweisungskonvertierung|-Jedes Objekt der SQL-Anweisung kann eine einzelne MySQL-Anweisung (z. B. DDL, DML und andere Arten von Anweisungen) enthalten, oder... END-Block.<br />-   **Mit mehreren Anweisungen Konvertierung: BEGIN... END-Block Konvertierung**SQL-Anweisung enthalten auch eine starten... END-Block, wie in der Definition von Prozedur, Funktion oder Trigger. Die Blöcke, die sollen die gleiche Weise konvertiert werden, die sie für die einzelnen Objekte der MySQL-Anweisung konvertiert werden.|  
  
## <a name="converting-mysql-database-objects"></a>Konvertieren von MySQL-Datenbank-Objekten  
Um MySQL-Datenbank-Objekte zu konvertieren, wählen Sie zuerst die Objekte, die Sie konvertieren möchten, und müssen dann SSMA, die die Konvertierung nicht ausgeführt. Anzeigen von ausgehenden Nachrichten bei der Konvertierung auf den **Ansicht** , wählen Sie im Menü **Ausgabe**.  
  
**So konvertieren Sie MySQL-Objekte in SQL Server oder SQL Azure-syntax**  
  
1.  Klicken Sie im MySQL-Metadaten-Explorer, erweitern Sie den MySQL-Server, und erweitern Sie dann **Datenbanken**.  
  
2.  Wählen Sie Objekte zu konvertieren:  
  
    -   Um alle Schemas zu konvertieren, wählen Sie das Kontrollkästchen neben **Datenbanken**.  
  
    -   Zum konvertieren, oder lassen Sie eine Datenbank, wählen Sie das Kontrollkästchen neben dem Datenbanknamen.  
  
    -   Konvertieren, oder lassen Sie eine Kategorie von Objekten, erweitern Sie ein Schema, und aktivieren Sie oder deaktivieren Sie das Kontrollkästchen neben der Kategorie.  
  
    -   Konvertieren, oder lassen Sie einzelne Objekte, erweitern Sie die Kategorieordner, und aktivieren Sie oder deaktivieren Sie das Kontrollkästchen neben dem Objekt.  
  
3.  Um alle ausgewählten Objekte zu konvertieren, Maustaste **Datenbanken** , und wählen Sie **Schema konvertieren**.  
  
    Sie können auch einzelne Objekte oder Kategorien von Objekten von der rechten Maustaste auf das Objekt oder der übergeordnete Ordner, und wählen Sie dann konvertieren **Schema konvertieren**.  
  
## <a name="viewing-conversion-problems"></a>Probleme bei der Konvertierung anzeigen  
Einige MySQL-Objekte können nicht konvertiert werden. Sie können die Abschlussraten für den Erfolg bestimmen, durch Anzeigen der Zusammenfassung Konvertierungsbericht.  
  
**Zum Anzeigen eines Übersichtsberichts**  
  
1.  Wählen Sie im MySQL-Metadaten-Explorer, **Datenbanken**.  
  
2.  Wählen Sie im rechten Bereich die **Bericht** Registerkarte.  
  
    Dieser Bericht zeigt die Zusammenfassung Bewertungsbericht für alle Datenbankobjekte, die bewertet oder konvertiert wurden. Sie können auch einen Zusammenfassungsbericht für einzelne Objekte anzeigen:  
  
    -   Um den Bericht für ein einzelnes Schema anzuzeigen, wählen Sie die Datenbank in der MySQL-Metadaten-Explorer aus.  
  
    -   Um den Bericht für ein einzelnes Objekt anzuzeigen, wählen Sie das Objekt in der MySQL-Metadaten-Explorer aus. Objekten, die Probleme bei der Konvertierung zu haben, ist ein rotes Fehlersymbol.  
  
Für Objekte, die Konvertierung fehlgeschlagen ist, können Sie die Syntax anzeigen, die die Konvertierungsfehler bewirkt, dass geführt haben.  
  
**Probleme beim Konvertieren der einzelnen anzeigen**  
  
1.  Erweitern Sie im MySQL-Metadaten-Explorer, **Datenbanken**.  
  
2.  Erweitern Sie die Datenbank, die ein rotes Fehlersymbol zeigt.  
  
3.  Erweitern Sie in der Datenbank einen Ordner mit einem roten Fehlersymbol aus.  
  
4.  Wählen Sie das Objekt mit einem roten Fehlersymbol.  
  
5.  Klicken Sie im rechten Bereich auf die **Bericht** Registerkarte.  
  
6.  Am oberen Rand der **Bericht** Registerkarte wird eine Dropdown-Liste. Wenn die Liste zeigt **Statistiken**, ändern Sie die Auswahl auf **Quelle**.  
  
    SSMA wird der Quellcode und verschiedene Schaltflächen direkt über dem Code angezeigt.  
  
7.  Klicken Sie auf die **nächsten Problem** Schaltfläche. Dies ist ein rotes Fehlersymbol mit einem Pfeil nach rechts.  
  
    SSMA wird es sich um den ersten problematisch Quellcode hervorheben, die, den Sie in das aktuelle Objekt findet.  
  
Für jedes Element, das nicht konvertiert werden konnten, müssen Sie bestimmen, was Sie mit diesem Objekt tun möchten:  
  
-   Sie können ändern, dass das Objekt in der MySQL-Datenbank zu entfernen oder die problematischen Code zu überarbeiten. Um den aktualisierten Code in SSMA laden zu können, müssen Sie die Metadaten zu aktualisieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
-   Sie können das Objekt von der Migration ausschließen. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer und MySQL-Metadaten-Explorer, deaktivieren Sie das Kontrollkästchen neben dem Element vor dem Laden der Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, und Migrieren von Daten aus MySQL.  
  
## <a name="next-step"></a>Nächster Schritt  
Im nächsten Schritt des Migrationsvorgangs [konvertiert Datenbankobjekte in SQL Server laden &#40;MySQLToSQL&#41;](../../ssma/mysql/loading-converted-database-objects-into-sql-server-mysqltosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von MySQL-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
