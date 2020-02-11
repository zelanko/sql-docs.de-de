---
title: MySQL-Datenbanken werden umgerechnet (mysqlto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ac21850b-fb32-4704-9985-5759b7c688c7
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 1ad4cbbdf80422f87c850c44e47f82899de4c82a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103049"
---
# <a name="converting-mysql-databases-mysqltosql"></a>Konvertieren von MySQL-Datenbanken (MySqlToSql)
Nachdem Sie eine Verbindung mit MySQL hergestellt, eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindung mit oder SQL Azure hergestellt und die Optionen für die Projekt-und Datenzuordnung festgelegt haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , können Sie MySQL-Datenbankobjekte in oder SQL Azure Datenbankobjekte konvertieren.  
  
## <a name="the-conversion-process"></a>Der Konvertierungsprozess  
Das Konvertieren von Datenbankobjekten übernimmt die Objekt Definitionen aus MySQL, konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie in ähnliche oder SQL Azure Objekte und lädt diese Informationen dann in die SSMA-Metadaten. Die Informationen werden nicht in die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]geladen. Anschließend können Sie die Objekte und deren Eigenschaften mithilfe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-metadatenexplorer anzeigen.  
  
Während der Konvertierung druckt SSMA Ausgabemeldungen im Ausgabebereich und Fehlermeldungen in den Fehlerliste Bereich. Bestimmen Sie anhand der Ausgabe-und Fehlerinformationen, ob Sie Ihre MySQL-Datenbanken oder den Konvertierungsprozess ändern müssen, um die gewünschten Konvertierungs Ergebnisse zu erhalten.  
  
## <a name="setting-conversion-options"></a>Festlegen von Konvertierungsoptionen  
Überprüfen Sie vor dem Konvertieren von Objekten die Projekt Konvertierungsoptionen im Dialogfeld **Projekteinstellungen** . Mit diesem Dialogfeld können Sie festlegen, wie SSMA Tabellen und Indizes konvertiert. Weitere Informationen finden Sie unter [Projekteinstellungen &#40;Konvertierung&#41; &#40;mysqltoisql&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
  
## <a name="conversion-results"></a>Konvertierungs Ergebnisse  
In der folgenden Tabelle werden die konvertierten MySQL-Objekte und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resultierenden Objekte angezeigt:  
  
|||  
|-|-|  
|**MySQL-Objekte**|**Resultierende SQL Server Objekte**|  
|Tabellen mit abhängigen Objekten, z. b. Indizes|SSMA erstellt Tabellen mit abhängigen Objekten. Die Tabelle wird mit allen Indizes und Einschränkungen konvertiert. Indizes werden in separate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte konvertiert.<br /><br />Die **Zuordnung räumlicher Datentypen** kann nur auf Tabellen Knotenebene ausgeführt werden.<br /><br />Weitere Informationen zu den Einstellungen für die Tabellen Konvertierung finden Sie unter [Konvertierungs Einstellungen](conversion-settings-mysqltosql.md) .|  
|Functions|Wenn die Funktion direkt in Transact-SQL konvertiert werden kann, erstellt SSMA eine Funktion. In einigen Fällen muss die Funktion in eine gespeicherte Prozedur konvertiert werden. Dies kann mithilfe der **Funktions Konvertierung** in den Projekteinstellungen erfolgen. In diesem Fall erstellt SSMA eine gespeicherte Prozedur und eine Funktion, die die gespeicherte Prozedur aufruft.<br /><br />**Angegebene Optionen:**<br /><br />Gemäß Projekteinstellungen konvertieren<br /><br />In Funktion konvertieren<br /><br />In gespeicherte Prozedur konvertieren<br /><br />Weitere Informationen zu den Einstellungen für die Funktions Konvertierung finden Sie unter [Konvertierungs Einstellungen](conversion-settings-mysqltosql.md) .|  
|Prozeduren|Wenn die Prozedur direkt in Transact-SQL konvertiert werden kann, erstellt SSMA eine gespeicherte Prozedur. In einigen Fällen muss eine gespeicherte Prozedur in einer autonomen Transaktion aufgerufen werden. In diesem Fall erstellt SSMA zwei gespeicherte Prozeduren: einen, der die Prozedur implementiert, und einen weiteren, der zum Aufrufen der implementierenden gespeicherten Prozedur verwendet wird.|  
|Datenbankkonvertierung|Datenbanken als MySQL-Objekte werden nicht direkt von SSMA für MySQL konvertiert. MySQL-Datenbanken werden eher wie Schema Namen behandelt, und alle physischen Parameter gehen bei der Konvertierung verloren. SSMA für MySQL verwendet [die Zuordnung von MySQL-Datenbanken zu SQL Server Schemas &#40;mysqltosql&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md) , um Objekte aus einer MySQL-Datenbank einem geeigneten SQL Server Database/Schema-Paar zuzuordnen.|  
|Umwandlungs Konvertierung|**SSMA erstellt Trigger auf der Grundlage der folgenden Regeln:**<br /><br />Vor dem Konvertieren von Triggern in anstelle von T-SQL-Triggern<br /><br />AFTER-Trigger werden in nach T-SQL-Triggern mit oder ohne Iterationen pro Zeilen konvertiert.|  
|Konvertierung anzeigen|SSMA erstellt Sichten mit abhängigen Objekten.|  
|Anweisungs Konvertierung|-Jedes SQL-Anweisungsobjekt kann eine einzelne MySQL-Anweisung enthalten (z. b. DDL-, DML-und andere Typen von Anweisungen) oder BEGIN... Endblock.<br />-   **Multistatement-Konvertierung: begin... **Die SQL-Anweisung für die End-Block Konvertierung kann auch einen Anfang enthalten... Beenden Sie den Block wie einen in der Prozedur, der Funktion oder der Triggerdefinition. Diese Blöcke sollten auf die gleiche Weise konvertiert werden, wie Sie für die einzelnen MySQL-Anweisungs Objekte konvertiert werden.|  
  
## <a name="converting-mysql-database-objects"></a>MySQL-Datenbankobjekte werden umgerechnet  
Um MySQL-Datenbankobjekte zu konvertieren, wählen Sie zuerst die Objekte aus, die Sie konvertieren möchten, und lassen Sie die Konvertierung von SSMA durchführen. Wenn Sie während der Konvertierung Ausgabemeldungen anzeigen möchten, wählen Sie im Menü **Ansicht** die Option **Ausgabe**aus.  
  
**So konvertieren Sie MySQL-Objekte in SQL Server-oder SQL Azure-Syntax**  
  
1.  Erweitern Sie im MySQL-metadatenexplorer den MySQL-Server, und erweitern Sie dann **Datenbanken**.  
  
2.  Zu konvertierende Objekte auswählen:  
  
    -   Aktivieren Sie das Kontrollkästchen neben **Datenbanken**, um alle Schemas zu konvertieren.  
  
    -   Aktivieren Sie das Kontrollkästchen neben dem Datenbanknamen, um eine Datenbank zu konvertieren oder auszulassen.  
  
    -   Wenn Sie eine Kategorie von Objekten konvertieren oder weglassen möchten, erweitern Sie ein Schema, und aktivieren bzw. deaktivieren Sie das Kontrollkästchen neben der Kategorie.  
  
    -   Wenn Sie einzelne Objekte konvertieren oder weglassen möchten, erweitern Sie den Ordner Category, und aktivieren oder deaktivieren Sie das Kontrollkästchen neben dem Objekt.  
  
3.  Zum Konvertieren aller ausgewählten Objekte klicken Sie mit der rechten Maustaste auf **Datenbanken** , und wählen Sie **Schema konvertieren**aus.  
  
    Sie können auch einzelne Objekte oder Kategorien von Objekten konvertieren, indem Sie mit der rechten Maustaste auf das Objekt oder seinen übergeordneten Ordner klicken und dann **Schema konvertieren**auswählen.  
  
## <a name="viewing-conversion-problems"></a>Anzeigen von Konvertierungs Problemen  
Einige MySQL-Objekte werden möglicherweise nicht konvertiert. Sie können die Erfolgsraten der Konvertierung ermitteln, indem Sie den Zusammenfassungs Bericht für die Zusammenfassung anzeigen  
  
**So zeigen Sie einen Zusammenfassungs Bericht an**  
  
1.  Wählen Sie im MySQL-metadatenexplorer **Datenbanken**aus.  
  
2.  Wählen Sie im rechten Bereich die Registerkarte **Bericht** aus.  
  
    Dieser Bericht zeigt den Zusammenfassungs Bewertungsbericht für alle Datenbankobjekte an, die bewertet oder konvertiert wurden. Sie können auch einen Zusammenfassungs Bericht für einzelne Objekte anzeigen:  
  
    -   Um den Bericht für ein einzelnes Schema anzuzeigen, wählen Sie die Datenbank im MySQL-metadatenexplorer aus.  
  
    -   Um den Bericht für ein einzelnes Objekt anzuzeigen, wählen Sie das Objekt im MySQL-metadatenexplorer aus. Bei Objekten, die Konvertierungsprobleme aufweisen, wird ein rotes Fehler Symbol angezeigt.  
  
Bei Objekten, die nicht erfolgreich konvertiert werden konnten, können Sie die Syntax anzeigen, die zu einem Konvertierungs Fehler geführt hat.  
  
**So zeigen Sie einzelne Konvertierungsprobleme an**  
  
1.  Erweitern Sie im MySQL-metadatenexplorer **Datenbanken**.  
  
2.  Erweitern Sie die Datenbank, in der ein rotes Fehler Symbol angezeigt wird.  
  
3.  Erweitern Sie unter der Datenbank einen Ordner mit einem roten Fehler Symbol.  
  
4.  Wählen Sie das Objekt mit einem roten Fehler Symbol aus.  
  
5.  Klicken Sie im rechten Bereich auf die Registerkarte **Bericht** .  
  
6.  Am oberen Rand der Registerkarte **Bericht** befindet sich eine Dropdown Liste. Wenn in der Liste **Statistiken**angezeigt werden, ändern Sie die Auswahl in **Quelle**.  
  
    SSMA zeigt den Quellcode und mehrere Schaltflächen direkt oberhalb des Codes an.  
  
7.  Klicken Sie auf die Schaltfläche **nächstes Problem** . Dabei handelt es sich um ein rotes Fehler Symbol mit einem Pfeil, der nach rechts zeigt.  
  
    SSMA hebt den ersten problematischen Quell Code hervor, der im aktuellen-Objekt gefunden wird.  
  
Sie müssen für jedes Element, das nicht konvertiert werden konnte, bestimmen, was Sie mit diesem Objekt tun möchten:  
  
-   Sie können das Objekt in der MySQL-Datenbank ändern, um problematischen Code zu entfernen oder zu überarbeiten. Um den aktualisierten Code in SSMA zu laden, müssen Sie die Metadaten aktualisieren. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit MySQL &#40;mysqlto SQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
-   Sie können das Objekt von der Migration ausschließen. Deaktivieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie in oder SQL Azure Metadaten-Explorer und MySQL-metadatenexplorer das Kontrollkästchen neben dem Element, bevor Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Objekte in laden oder SQL Azure und Daten aus MySQL migrieren.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrations Vorgangs ist das [Laden von konvertierten Datenbankobjekten in SQL Server &#40;mysqldesql&#41;](../../ssma/mysql/loading-converted-database-objects-into-sql-server-mysqltosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von MySQL-Datenbanken zu SQL Server-Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
