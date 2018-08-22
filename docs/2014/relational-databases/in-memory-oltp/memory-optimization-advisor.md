---
title: Ratgeber für die Speicheroptimierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.memoryoptimizationwizard.f1
- swb.memoryoptimizationwizard.f1
ms.assetid: 181989c2-9636-415a-bd1d-d304fc920b8a
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2f5f45037ec9c988a2c7b95df37fd338d98ce7db
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393009"
---
# <a name="memory-optimization-advisor"></a>Ratgeber für die Speicheroptimierung
  Das Berichtstool für Transaktionsleistung (siehe [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) informiert Sie darüber, welche Tabellen in der Datenbank von einer Portierung zu In-Memory OLTP profitieren. Nachdem Sie eine Tabelle identifiziert haben, die Sie zur Verwendung In-Memory OLTP portieren möchten, können Sie den Ratgeber für die Speicheroptimierung verwenden, der Sie bei der Migration der datenträgerbasierten Datenbanktabelle zu In-Memory OLTP unterstützt.  
  
 Stellen Sie zunächst eine Verbindung mit der Instanz her, die die datenträgerbasierte Datenbanktabelle enthält. Die Verbindung kann mit einer Instanz von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] oder [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] hergestellt werden. Wenn Sie jedoch einen Migrationsvorgang mit dem Ratgeber ausführen möchten, müssen Sie eine Verbindung mit einer [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] -Instanz herstellen, für die In-Memory OLTP aktiviert ist. Weitere Informationen zu den Anforderungen für In-Memory OLTP finden Sie unter [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md).  
  
 Weitere Informationen zu Migrationsmethoden finden Sie unter [In-Memory OLTP − Allgemeine Arbeitsauslastungsmuster und Überlegungen zur Migration](http://msdn.microsoft.com/library/dn673538.aspx).  
  
## <a name="walkthrough-using-the-memory-optimization-advisor"></a>Exemplarische Vorgehensweise: Ratgeber für die Speicheroptimierung  
 Klicken Sie im **Objekt-Explorer**mit der rechten Maustaste auf die Tabelle, die Sie konvertieren möchten, und wählen Sie **Ratgeber für die Speicheroptimierung**aus. Daraufhin wird die Willkommensseite für **Ratgeber für die Speicheroptimierung von Tabellen**angezeigt.  
  
### <a name="memory-optimization-checklist"></a>Prüfliste für die Speicheroptimierung  
 Wenn Sie auf der Willkommensseite für den **Ratgeber für die Speicheroptimierung von Tabellen** auf **Weiter**klicken, wird die Prüfliste für die Speicheroptimierung angezeigt. Nicht alle Funktionen in einer datenträgerbasierten Tabelle werden durch speicheroptimierte Tabellen unterstützt. Der Prüfliste für die Speicheroptimierung können Sie entnehmen, ob die datenträgerbasierte Tabelle Funktionen nutzt, die nicht mit einer speicheroptimierten Tabelle kompatibel sind. Die datenträgerbasierte Tabelle wird vom **Ratgeber für die Speicheroptimierung von Tabellen** nicht geändert, sodass sie zur Verwendung von In-Memory-OLTP migriert werden kann. Um die Migration fortzusetzen, müssen Sie diese Änderungen vornehmen. Bei jeder gefundenen Inkompatibilität zeigt der **Ratgeber für die Speicheroptimierung von Tabellen** einen Link zu Informationen an, die Sie beim Ändern datenträgerbasierter Tabellen unterstützen.  
  
 Wenn Sie eine Liste dieser Inkompatibilitäten aufbewahren möchten, um die Migration zu planen, klicken Sie zum Generieren einer HTML-Liste auf **Bericht generieren** .  
  
 Wenn die Tabelle über keine Inkompatibilitäten verfügt und Sie mit einer [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] -Instanz mit In-Memory-OLTP verbunden sind, klicken Sie auf **Weiter**.  
  
### <a name="memory-optimization-warnings"></a>Warnmeldungen für die Speicheroptimierung  
 Die nächste Seite Warnmeldungen für die Speicheroptimierung enthält eine Liste der Probleme, die die Tabellenmigration zur Verwendung von In-Memory OLTP nicht verhindern. Das kann jedoch zu fehlerhaftem oder unerwartetem Verhalten anderer Objekte (z. B. gespeicherter Prozeduren oder CLR-Funktionen) führen.  
  
 Die ersten Warnungen in der Liste dienen zur Information und können sich auf die Tabelle beziehen oder auch nicht. Über die Links in der rechten Tabellenspalte gelangen Sie zu weiteren Informationen.  
  
 In der Warnungstabelle werden außerdem mögliche Warnbedingungen angezeigt, die auf die Tabelle nicht zutreffen.  
  
 Warnungen, die eine Aktion erfordern, sind in der linken Spalte mit einem gelben Dreieck gekennzeichnet. Wenn solche Warnungen vorliegen, sollten Sie die Migration beenden, die Ursache der Warnungen beseitigen und den Vorgang neu starten. Wenn die Warnungen nicht aufgelöst werden, kann die migrierte Tabelle einen Fehler verursachen.  
  
 Klicken Sie auf **Bericht generieren** , um einen HTML-Bericht dieser Warnungen zu generieren. Klicken Sie auf **Weiter** , um den Vorgang fortzusetzen.  
  
### <a name="review-optimization-options"></a>Optimierungsoptionen überprüfen  
 Auf dem folgenden Bildschirm können Sie Optionen für die Migration zu In-Memory OLTP ändern:  
  
 Speicheroptimierte Dateigruppe  
 Der Name für die speicheroptimierte Dateigruppe. Eine Datenbank muss eine speicheroptimierte Dateigruppe mit mindestens einer Datei enthalten, bevor eine speicheroptimierte Tabelle erstellt werden kann.  
  
 Wenn Sie über keine speicheroptimierte Dateigruppe verfügen, können Sie den Standardnamen ändern. Speicheroptimierte Dateigruppen können nicht gelöscht werden. Das Vorhandensein einer speicheroptimierten Dateigruppe kann dazu führen, dass einige Funktionen auf Datenbankebene wie AUTO CLOSE und die Datenbankspiegelung deaktiviert werden.  
  
 Wenn eine Datenbank bereits eine speicheroptimierte Dateigruppe besitzt, enthält dieses Feld bereits den Namen der Dateigruppe und Sie können den Wert in diesem Feld nicht ändern.  
  
 Logischer Dateiname und -pfad  
 Der Name der Datei, in der die speicheroptimierte Tabelle enthalten ist. Eine Datenbank muss eine speicheroptimierte Dateigruppe mit mindestens einer Datei enthalten, bevor eine speicheroptimierte Tabelle erstellt werden kann.  
  
 Wenn keine speicheroptimierte Dateigruppe vorhanden ist, können Sie den Standardnamen und -pfad der zu erstellenden Daten am Ende des Migrationsprozesses ändern.  
  
 Wenn Sie über eine speicheroptimierte Dateigruppe verfügen, sind diese Felder bereits mit Werten aufgefüllt. Die Werte können nicht geändert werden.  
  
 Ursprüngliche Tabelle umbenennen in  
 Am Ende des Migrationsprozesses wird eine neue speicheroptimierte Tabelle mit dem aktuellen Namen der Tabelle erstellt. Um einen Namenskonflikt zu vermeiden, muss die aktuelle Tabelle umbenannt werden. Sie können den Namen in diesem Feld ändern.  
  
 Geschätzte aktuelle Speicherkosten (MB)  
 Der Ratgeber für die Speicheroptimierung schätzt die von der neuen speicheroptimierten Tabelle genutzte Arbeitsspeicherkapazität. Die Schätzung basiert auf den Metadaten der datenträgerbasierten Tabelle. Die Berechnung der Tabellengröße wird in dem Artikel [Tabellen- und Zeilengröße in speicheroptimierten Tabellen](table-and-row-size-in-memory-optimized-tables.md)erläutert.  
  
 Wenn nicht genügend Arbeitsspeicher zugewiesen wird, tritt beim Migrationsprozess ein Fehler auf.  
  
 Tabellendaten auch in die neue speicheroptimierte Tabelle kopieren  
 Wählen Sie diese Option aus, wenn Sie auch die Daten der aktuellen Tabelle in die neue speicheroptimierte Tabelle verschieben möchten. Wenn diese Option nicht ausgewählt ist, wird die neue speicheroptimierte Tabelle ohne Zeilen erstellt.  
  
 Die Tabelle wird standardmäßig als dauerhafte Tabelle migriert  
 In-Memory OLTP unterstützt nicht dauerhafte Tabellen, die gegenüber dauerhaften speicheroptimierten Tabellen eine höhere Leistung aufweisen. Die Daten in einer nicht dauerhaften Tabelle gehen beim Serverneustart jedoch verloren.  
  
 Wenn diese Option ausgewählt ist, erstellt der Ratgeber für die Speicheroptimierung anstatt einer dauerhaften eine nicht dauerhafte Tabelle.  
  
> [!WARNING]  
>  Wählen Sie diese Option nur aus, wenn Sie das mit nicht dauerhaften Tabellen verbundene Datenverlustrisiko in Kauf nehmen.  
  
 Klicken Sie auf **Weiter** , um den Vorgang fortzusetzen.  
  
### <a name="review-primary-key-conversion"></a>Konvertierung des primären Schlüssels überprüfen  
 Der nächste Bildschirm lautet **Konvertierung des primären Schlüssels überprüfen**. Der Ratgeber für die Speicheroptimierung stellt fest, ob die Tabelle einen oder mehrere primäre Schlüssel enthält und füllt die Spaltenliste anhand von Primärschlüssel-Metadaten auf. Wenn Sie eine Migration zu einer dauerhaften speicheroptimierten Tabelle ausführen möchten, müssen Sie einen Primärschlüssel erstellen.  
  
 Wenn kein Primärschlüssel vorhanden ist und die Tabelle in eine nicht dauerhafte Tabelle migriert wird, wird dieser Bildschirm nicht angezeigt.  
  
 Bei Textspalten (mit dem Typ `char`, `nchar`, `varchar` und `nvarchar`) müssen Sie eine entsprechende Sortierung auswählen. In-Memory OLTP unterstützt BIN2-Sortierungen nur für Spalten in einer speicheroptimierten Tabelle. Sortierungen mit zusätzlichen Zeichen werden nicht unterstützt. Unter [Collations and Code Pages](../../database-engine/collations-and-code-pages.md) finden Sie Informationen zu den unterstützten Sortierungen und den möglichen Auswirkungen, die eine Änderung der Sortierung mit sich bringen kann.  
  
 Sie können die folgenden Parameter für den Primärschlüssel konfigurieren:  
  
 Neuen Dateinamen für den Primärschlüssel auswählen  
 Der Primärschlüsselname für diese Tabelle muss innerhalb der Datenbank eindeutig sein. Sie können den Namen des Primärschlüssels hier ändern.  
  
 Typ des primären Schlüssels auswählen  
 In-Memory OLTP unterstützt zwei Indextypen für eine speicheroptimierte Tabelle:  
  
-   Einen NONCLUSTERED HASH-Index. Dieser Index eignet sich am besten für Indizes mit zahlreichen Punktsuchen. Sie können die Bucketanzahl für den Index im Feld **Bucketanzahl** konfigurieren.  
  
-   Ein NONCLUSTERED-Index. Dieser Indextyp eignet sich am besten für Indizes mit zahlreichen Bereichsabfragen. Sie können die Sortierreihenfolge jeder Spalte in der Liste **Sortierspalte und -reihenfolge** konfigurieren.  
  
 Welcher Indextyp am besten für den Primärschlüssel geeignet ist, erfahren Sie unter [Hashindizes](../../database-engine/hash-indexes.md).  
  
 Klicken Sie auf **Weiter** , nachdem Sie die Primärschlüsseloptionen ausgewählt haben.  
  
### <a name="review-index-conversion"></a>Indexkonvertierung überprüfen  
 Die nächste Seite lautet **Indexkonvertierung überprüfen**. Der Ratgeber für die Speicheroptimierung erkennt, ob einer oder mehrere Indizes in der Tabelle enthalten sind und füllt die Spaltenliste und den Datentyp mit Werten auf. Die Parameter, die Sie auf der Seite **Indexkonvertierung überprüfen** konfigurieren können, ähneln denen auf der vorangehenden Seite **Konvertierung des primären Schlüssels überprüfen** .  
  
 Wenn die Tabelle nur über einen Primärschlüssel verfügt und zu einer dauerhaften Tabelle migriert wird, wird der Bildschirm nicht angezeigt.  
  
 Nachdem Sie für jeden Index in der Tabelle eine Entscheidung getroffen haben, klicken Sie auf **Weiter**.  
  
### <a name="verify-migration-actions"></a>Migrationsaktionen überprüfen  
 Die nächste Seite lautet **Migrationsaktionen überprüfen**. Um ein Skript für den Migrationsvorgang zu erstellen, klicken Sie auf **Skript** , um ein [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript zu generieren. Sie können das Skript anschließend ändern und ausführen. Klicken Sie auf **Migrieren** , um die Tabellenmigration zu starten.  
  
 Aktualisieren Sie nach Ende des Prozesses den **Objekt-Explorer** , um die neue speicheroptimierte Tabelle und die alte datenträgerbasierte Tabelle anzuzeigen. Sie können die alte Tabelle beibehalten oder löschen.  
  
## <a name="see-also"></a>Siehe auch  
 [Migrieren zu In-Memory OLTP](migrating-to-in-memory-oltp.md)  
  
  
