---
title: Always Encrypted mit Secure Enclaves
description: Erfahren Sie mehr zu Always Encrypted mit dem Feature „Secure Enclaves“ für SQL Server.
ms.custom: seo-lt-2019
ms.date: 10/31/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 6e750070f51dc6cba1b035e9426d9814e4fd1b67
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "75558027"
---
# <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted mit Secure Enclaves
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]
 
Always Encrypted mit Secure Enclaves bietet zusätzliche Funktionalität für das Feature [Always Encrypted](always-encrypted-database-engine.md).

Always Encrypted wurde in SQL Server 2016 eingeführt und schützt vertrauliche Daten vor Schadsoftware und dem Zugriff *nicht autorisierter* SQL Server-Benutzer mit hohen Berechtigungen. Nicht autorisierte Benutzer mit hohen Berechtigungen sind Datenbankadministratoren, Computeradministratoren, Cloudadministratoren sowie alle anderen Benutzer, die legitim auf Serverinstanzen, Hardware und ähnliches zugreifen, aber keine Zugriff auf einige oder alle der tatsächlichen Daten haben sollten.  

Ohne die in diesem Artikel erläuterten Erweiterungen schützt Always Encrypted die Daten, indem das Feature die Daten auf Clientseite verschlüsselt und niemals zulässt, dass die Daten oder die zugehörigen kryptografischen Schlüssel als Klartext in der SQL Server-Engine angezeigt werden. Daher ist die Funktionalität von verschlüsselten Spalten innerhalb der Daten stark eingeschränkt. Die einzigen Vorgänge, die SQL Server für verschlüsselte Daten ausführen kann, sind Gleichheitsvergleiche (und diese waren nur bei deterministischer Verschlüsselung verfügbar). Alle anderen Vorgänge, beispielweise kryptografische Vorgänge (anfängliche Datenverschlüsselung oder Schlüsselrotation), sowie umfangreiche Berechnungen (z. B. Musterabgleich) werden innerhalb der Datenbank nicht unterstützt. Benutzer müssen ihre Daten aus der Datenbank verschieben, um diese Vorgänge auf Clientseite auszuführen.

Always Encrypted *mit Secure Enclaves* beseitigt diese Einschränkungen, indem Berechnungen für Klartextdaten innerhalb einer Secure Enclave auf Serverseite zugelassen werden. Eine Secure Enclave ist eine geschützte Arbeitsspeicherregion im SQL Server-Prozess und fungiert als vertrauenswürdige Ausführungsumgebung für die Verarbeitung vertraulicher Daten in der SQL Server-Engine. Eine Secure Enclave wird dem Rest von SQL Server und anderen Prozessen auf dem Hostcomputer als Blackbox angezeigt. Es gibt keine Möglichkeit, Daten oder Code innerhalb der Enclave von außen anzuzeigen, auch nicht mit einem Debugger.  


Always Encrypted verwendet Secure Enclaves wie im folgenden Diagramm veranschaulicht:

![Datenfluss](./media/always-encrypted-enclaves/ae-data-flow.png)



Beim Analysieren der Abfrage einer Anwendung ermittelt die SQL Server-Engine, ob die Abfrage Vorgänge für verschlüsselte Daten enthält, für die die Verwendung der Secure Enclave erforderlich ist. Bei Abfragen, für die auf die Secure Enclave zugegriffen werden muss, gilt Folgendes:

- Der Clienttreiber sendet die für die Vorgänge erforderlichen Spaltenverschlüsselungsschlüssel an die Secure Enclave (oder einen sicheren Kanal). 
- Dann übermittelt der Clienttreiber die Abfrage zusammen mit den verschlüsselten Abfrageparametern zur Ausführung.

Während der Verarbeitung der Abfrage werden weder die Daten noch die Spaltenverschlüsselungsschlüssel außerhalb der Secure Enclave als Klartext in der SQL Server-Engine verfügbar gemacht. Die SQL Server-Engine delegiert kryptografische Vorgänge und Berechnungen für verschlüsselte Spalten an die Secure Enclave. Bei Bedarf entschlüsselt die Secure Enclave die Abfrageparameter und/oder die in verschlüsselten Spalten gespeicherten Daten und führt die angeforderten Vorgänge aus.

In [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] verwendet Always Encrypted über [Virtualisierungsbasierte Sicherheit (VBS)](https://www.microsoft.com/security/blog/2018/06/05/virtualization-based-security-vbs-memory-enclaves-data-protection-through-isolation/) abgesicherte Secure Enclaves (auch als VSM-Enclaves bezeichnet) im Windows-Arbeitsspeicher.

## <a name="why-use-always-encrypted-with-secure-enclaves"></a>Was spricht für die Verwendung von Always Encrypted mit Secure Enclaves?

Mit Secure Enclaves schützt Always Encrypted die Vertraulichkeit von Daten und bietet gleichzeitig folgende Vorteile:

- **Direkte Verschlüsselung**: Kryptografische Vorgänge für vertrauliche Daten, wie z.B. die anfängliche Datenverschlüsselung oder das Rotieren eines Spaltenverschlüsselungsschlüssels, werden innerhalb der Secure Enclave ausgeführt und erfordern kein Verschieben der Daten an einen Ort außerhalb der Datenbank. Sie können die direkte Verschlüsselung mit der Transact-SQL-Anweisung ALTER TABLE ausführen. Sie benötigen keine Tools wie etwa den Always Encrypted-Assistenten in SSMS oder das PowerShell-Cmdlet „Set-SqlColumnEncryption“.

- **Umfangreiche Berechnungen (Vorschau)** : Vorgänge in verschlüsselten Spalten, wie z.B. Musterabgleich (das LIKE-Prädikat) und Bereichsvergleiche, werden innerhalb der Secure Enclave unterstützt. Damit lässt sich Always Encrypted für eine Vielzahl von Anwendungen und Szenarien verwenden, bei denen solche Berechnungen innerhalb des Datenbanksystems ausgeführt werden müssen.

## <a name="secure-enclave-attestation"></a>Nachweis von Secure Enclaves

Die Secure Enclave in der SQL Server-Engine kann im Klartextformat auf vertrauliche Daten, die in verschlüsselten Datenbankspalten gespeichert sind, sowie auf die entsprechenden Spaltenverschlüsselungsschlüssel zugreifen. Bevor eine Abfrage mit Enclave-Berechnungen an SQL Server übermittelt wird, muss der Clienttreiber innerhalb der Anwendung überprüfen, ob es sich bei der Secure Enclave um eine echte Enclave handelt, die auf einer bestimmten Technologie basiert (z.B. VBS). Darüber hinaus muss der Treiber überprüfen, ob der Code, der in der Enclave ausgeführt wird, für die Ausführung in der Enclave signiert wurde. 

Der Prozess der Überprüfung der Enclave wird als **Enclave-Nachweis** bezeichnet und erfordert, dass sowohl ein Clienttreiber innerhalb der Anwendung als auch SQL Server einen externen Nachweisdienst kontaktiert. Die genauen Merkmale des Nachweisprozesses richten sich nach der Enclave-Technologie und dem Nachweisdienst.

Der Nachweisprozess, den SQL Server für Secure Enclaves für VBS in [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] unterstützt, ist der Windows Defender System Guard-Runtimenachweis, bei dem Host Guardian Service (HGS) als Nachweisdienst verwendet wird. Sie müssen HGS in Ihrer Umgebung konfigurieren und den Computer, auf dem Ihre SQL Server-Instanz gehostet wird, in HGS registrieren. Sie müssen auch Ihre Clientanwendungen oder -tools (z.B. SQL Server Management Studio) mit einem HGS-Nachweis konfigurieren.

## <a name="supported-client-drivers"></a>Unterstützte Clienttreiber

Um Always Encrypted mit Secure Enclaves verwenden zu können, muss eine Anwendung einen Clienttreiber nutzen, der dieses Feature unterstützt. Sie müssen die Anwendung sowie den Clienttreiber konfigurieren, um Enclave-Berechnungen und Enclave-Nachweise zu aktivieren. Weitere Informationen, einschließlich der Liste der unterstützten Clienttreiber, finden Sie unter [Always Encrypted mit Secure Enclaves](always-encrypted-enclaves.md).

## <a name="enclave-enabled-keys"></a>Enclave-fähige Schlüssel

Always Encrypted mit Secure Enclave führt das Konzept der Enclave-fähigen Schlüssel ein:

- **Enclave-fähiger Spaltenhauptschlüssel**: Ein Spaltenhauptschlüssel, für den die ENCLAVE_COMPUTATIONS-Eigenschaft im Spaltenhauptschlüssel-Metadatenobjekt in der Datenbank angegeben ist. Das Spaltenhauptschlüssel-Metadatenobjekt muss auch eine gültige Signatur der Metadateneigenschaften enthalten.
- **Enclave-fähiger Spaltenverschlüsselungsschlüssel**: Ein Spaltenverschlüsselungsschlüssel, der mit einem Enclave-fähigen Spaltenhauptschlüssel verschlüsselt ist.

Wenn die SQL Server-Engine feststellt, dass die in einer Abfrage angegebenen Vorgänge innerhalb der Secure Enclave ausgeführt werden müssen, fordert die Engine den Clienttreiber auf, die für die Berechnungen erforderlichen Spaltenverschlüsselungsschlüssel für die Secure Enclave freizugeben. Der Clienttreiber gibt die Spaltenverschlüsselungsschlüssel nur dann frei, wenn diese Enclave-fähig sind (also mit Enclave-fähigen Spaltenhauptschlüsseln verschlüsselt wurden) und ordnungsgemäß signiert wurden. Andernfalls kann die Abfrage nicht ausgeführt werden.

Weitere Informationen finden Sie unter [Verwalten von Schlüsseln für Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-manage-keys.md).

## <a name="enclave-enabled-columns"></a>Enclave-fähige Spalten

Eine Enclave-fähige Spalte ist eine Datenbankspalte, die mit einem Enclave-fähigen Spaltenverschlüsselungsschlüssel verschlüsselt ist. Welche Funktionalität für eine Enclave-fähige Spalte verfügbar ist, richtet sich nach dem von der Spalte verwendeten Verschlüsselungstyp.

- **Deterministische Verschlüsselung**: Enclave-fähige Spalten, die die deterministische Verschlüsselung verwenden, unterstützen die direkte Verschlüsselung, aber keine anderen Vorgänge innerhalb der Secure Enclave. Gleichheitsvergleiche werden unterstützt. Dafür wird jedoch außerhalb der Enclave der Chiffretext verglichen.  
- **Verschlüsselung nach dem Zufallsprinzip**: Enclave-fähige Spalten, die die Verschlüsselung nach dem Zufallsprinzip verwenden, unterstützen die direkte Verschlüsselung sowie umfangreiche Berechnungen innerhalb der Secure Enclave. Zu den unterstützten umfangreichen Berechnungen zählen Musterabgleich und [Vergleichsoperatoren](../../../t-sql/language-elements/comparison-operators-transact-sql.md), einschließlich Gleichheitsvergleich.

Weitere Informationen zu Verschlüsselungstypen finden Sie unter [Always Encrypted-Kryptografie](always-encrypted-cryptography.md).

Die folgende Tabelle fasst die für verschlüsselte Spalten verfügbaren Funktionen zusammen – je nachdem, ob die Spalten Enclave-fähige Spaltenverschlüsselungsschlüssel und einen Verschlüsselungstyp verwenden.

| **Vorgang**| **Spalte ist NICHT Enclave-fähig** |**Spalte ist NICHT Enclave-fähig**| **Spalte ist Enclave-fähig**  |**Spalte ist Enclave-fähig** |
|:---|:---|:---|:---|:---|
| | **Verschlüsselung nach dem Zufallsprinzip**  | **Deterministische Verschlüsselung**     | **Verschlüsselung nach dem Zufallsprinzip**      | **Deterministische Verschlüsselung**     |
| **Direkte Verschlüsselung** | Nicht unterstützt  | Nicht unterstützt   | Unterstützt         | Unterstützt    |
| **Gleichheitsvergleich**   | Nicht unterstützt | Außerhalb der Enclave unterstützt | Unterstützt (innerhalb der Enclave) | Außerhalb der Enclave unterstützt |
| **Vergleichsoperatoren zusätzlich zum Gleichheitsvergleich** | Nicht unterstützt  | Nicht unterstützt   | Unterstützt      | Nicht unterstützt     |
| **LIKE**    | Nicht unterstützt      | Nicht unterstützt    | Unterstützt     | Nicht unterstützt    |

Die direkte Verschlüsselung umfasst Unterstützung für die folgenden Vorgänge innerhalb der Enclave:

- Anfängliche Verschlüsselung von Daten, die in einer vorhandenen Spalte gespeichert sind.
- Erneute Verschlüsselung von vorhandenen Daten in einer Spalte. Beispiele:
  
  - Rotieren des Spaltenverschlüsselungsschlüssels (erneute Verschlüsselung der Spalte mit einem neuen Schlüssel).
  - Ändern des Verschlüsselungstyps.  

- Entschlüsseln von Daten, die in einer verschlüsselten Spalte gespeichert sind (Konvertieren der Spalte in eine Klartextspalte).

Um die direkte Verschlüsselung zu ermöglichen, müssen die Spaltenverschlüsselungsschlüssel, die an den kryptografischen Vorgängen beteiligt sind, Enclave-fähig sein:

- Anfängliche Verschlüsselung: Der Spaltenverschlüsselungsschlüssel für die zu verschlüsselnde Spalte muss Enclave-fähig sein.
- Erneute Verschlüsselung: Sowohl der aktuelle als auch der neue Spaltenverschlüsselungsschlüssel (sofern Letzterer sich vom aktuellen Schlüssel unterscheidet) müssen Enclave-fähig sein.
- Entschlüsselung: Der aktuelle Spaltenverschlüsselungsschlüssel der Spalte muss Enclave-fähig sein.

### <a name="indexes-on-enclave-enabled-columns-using-randomized-encryption"></a>Indizes für Enclave-fähige Spalten mit zufälliger Verschlüsselung
Sie können nicht gruppierte Indizes auf Enclave-fähigen Spalten mit zufälliger Verschlüsselung erstellen, um umfangreiche Abfragen schneller ausführen zu können. Um sicherzustellen, dass ein mit zufälliger Verschlüsselung verschlüsselter Index in einer Spalte keine sensiblen Daten offenlegt und gleichzeitig für die Verarbeitung von Abfragen innerhalb der Enclave geeignet ist, werden die Schlüsselwerte in der Indexdatenstruktur (B-Struktur) nach ihren Klartextwerten verschlüsselt und sortiert. Wenn der Abfrageexecutor in der SQL Server-Engine einen Index auf einer verschlüsselten Spalte für Berechnungen innerhalb der Enclave verwendet, durchsucht er den Index nach bestimmten, in der Spalte gespeicherten Werten. Bei jeder Suche werden möglicherweise mehrere Vergleiche ausgeführt. Der Abfrageexecutor delegiert jeden Vergleich an die Enclave, die einen in der Spalte gespeicherten Wert und den zu vergleichenden verschlüsselten Indexschlüsselwert entschlüsselt, den Vergleich im Klartext durchführt und das Ergebnis des Vergleichs an den Executor zurückgibt. 

Das Erstellen von Indizes auf Spalten, die zufällige Verschlüsselung verwenden und nicht Enclave-fähig sind, wird weiterhin nicht unterstützt.

Weitere Informationen finden Sie unter [Erstellen und Verwenden von Indizes in Spalten mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-create-use-indexes.md). Allgemeine Informationen zur Funktionsweise der Indizierung in SQL Server, die nicht speziell für Always Encrypted gelten, finden Sie unter [Beschreibung von gruppierten und nicht gruppierten Indizes](../../indexes/clustered-and-nonclustered-indexes-described.md).

#### <a name="database-recovery"></a>Datenbankwiederherstellung

Wenn eine SQL Server-Instanz ausfällt, können ihre Datenbanken in einem Zustand verbleiben, in dem die Datendateien einige Änderungen durch unvollständige Transaktionen enthalten können. Wenn die Instanz gestartet wird, führt sie einen Prozess namens [Datenbankwiederherstellung](../../logs/the-transaction-log-sql-server.md#recovery-of-all-incomplete-transactions-when--is-started) aus, bei dem jede im Transaktionsprotokoll gefundene unvollständige Transaktion zurückgesetzt wird, um sicherzustellen, dass die Integrität der Datenbank erhalten bleibt. Wenn eine unvollständige Transaktion Änderungen an einem Index vorgenommen hat, müssen diese ebenfalls rückgängig gemacht werden. Beispielsweise müssen einige Schlüsselwerte im Index entfernt oder neu eingefügt werden.

> [!IMPORTANT]
> Microsoft empfiehlt dringend, die [Schnellere Datenbankwiederherstellung (ADR)](../../backup-restore/restore-and-recovery-overview-sql-server.md#adr) für Ihre Datenbank zu aktivieren, **bevor** Sie den ersten Index auf einer Enclave-fähigen Spalte verwenden, die mit zufälliger Verschlüsselung verschlüsselt wurde.

Beim herkömmlichen [Datenbankwiederherstellungsprozess](https://docs.microsoft.com/azure/sql-database/sql-database-accelerated-database-recovery#the-current-database-recovery-process) (gemäß dem [ARIES](https://people.eecs.berkeley.edu/~brewer/cs262/Aries.pdf)-Wiederherstellungsmodell) muss SQL Server zum Rückgängigmachen einer Änderung an einem Index warten, bis eine Anwendung den Spaltenverschlüsselungsschlüssel für die Spalte an die Enclave übermittelt. Dies kann sehr lange dauern. ADR reduziert die Anzahl der Vorgänge zum Rückgängigmachen von Änderungen, die verschoben werden müssen, da ein Spaltenverschlüsselungsschlüssel im Cache innerhalb der Enclave nicht verfügbar ist. Infolgedessen wird die Verfügbarkeit der Datenbank erheblich erhöht, indem die Wahrscheinlichkeit, dass eine neue Transaktion blockiert wird, minimiert wird. Wenn ADR aktiviert ist, benötigt SQL Server möglicherweise immer noch einen Spaltenverschlüsselungsschlüssel, um die Bereinigung alter Datenversionen abzuschließen, aber er erledigt dies als Hintergrundaufgabe, die sich nicht auf die Verfügbarkeit der Datenbank oder Benutzertransaktionen auswirkt. Es kann jedoch vorkommen, dass Fehlermeldungen im Fehlerprotokoll angezeigt werden, die auf fehlgeschlagene Bereinigungsvorgänge aufgrund eines fehlenden Spaltenverschlüsselungsschlüssels hinweisen.

### <a name="indexes-on-enclave-enabled-columns-using-deterministic-encryption"></a>Indizes auf Enclave-fähige Spalten mit deterministischer Verschlüsselung

Ein Index auf einer Spalte mit deterministischer Verschlüsselung wird basierend auf Chiffretext (nicht Klartext) sortiert, unabhängig davon, ob die Spalte Enclave-fähig ist oder nicht.

## <a name="security-considerations"></a>Überlegungen zur Sicherheit

Die folgenden Sicherheitsaspekte sind für Always Encrypted mit Secure Enclaves zu beachten.

- Die Sicherheit Ihrer Daten innerhalb der Enclave hängt von einem Nachweisprotokoll und einem Nachweisdienst ab. Daher müssen Sie sicherstellen, dass der Nachweisdienst und die Nachweisrichtlinien, die der Dienst durchsetzt, von einem vertrauenswürdigen Administrator verwaltet werden. Darüber hinaus unterstützen die Nachweisdienste in der Regel verschiedene Richtlinien und Nachweisprotokolle, von denen einige eine minimale Überprüfung der Enclave und ihrer Umgebung durchführen und für Test- und Entwicklungszwecke konzipiert sind. Halten Sie sich genau an die für Ihren Nachweisdienst spezifischen Richtlinien, um sicherzustellen, dass Sie die empfohlenen Konfigurationen und Richtlinien für Ihre Produktionsumgebungen verwenden. 
- Die Verschlüsselung einer Spalte mit zufälliger Verschlüsselung mit einem Enclave-fähigen CEK kann dazu führen, dass die Reihenfolge der in der Spalte gespeicherten Daten verloren geht, da solche Spalten Bereichsvergleiche unterstützen. Wenn beispielsweise eine verschlüsselte Spalte, die Gehälter von Mitarbeitern enthält, einen Index verwendet, könnte ein böswilliger DBA den Index scannen, um den maximalen verschlüsselten Wert für das Gehalt zu finden und eine Person mit dem maximalen Gehalt zu identifizieren (vorausgesetzt, der Name der Person ist nicht verschlüsselt). 
- Wenn Sie Always Encrypted verwenden, um sensible Daten vor unbefugtem Zugriff durch DBAs zu schützen, sollten Sie die Spaltenhauptschlüssel oder Spaltenverschlüsselungsschlüssel nicht an die DBAs weitergeben. Ein DBA kann Indizes auf verschlüsselten Spalten verwalten, ohne direkten Zugriff auf die Schlüssel zu haben, indem er den Cache der Spaltenverschlüsselungsschlüssel innerhalb der Enclave nutzt.

## <a name="considerations-for-availability-groups-and-database-migration"></a><a name="anchorname-1-considerations-availability-groups-db-migration"></a> Überlegungen zu Verfügbarkeitsgruppen und Datenbankmigration

Bei der Konfiguration einer Always On-Verfügbarkeitsgruppe, die für die Unterstützung von Abfragen mit Enclaves erforderlich ist, müssen Sie sicherstellen, dass alle SQL Server-Instanzen, die die Datenbanken in der Verfügbarkeitsgruppe hosten, Always Encrypted mit Secure Enclaves unterstützen und eine Enclave konfiguriert ist. Wenn die primäre Datenbank Enclaves unterstützt, eine sekundäre Replik jedoch nicht, schlägt jede Abfrage fehl, die versucht, die Funktionalität von Always Encrypted mit Secure Enclaves zu nutzen.

Wenn Sie eine Sicherungsdatei einer Datenbank wiederherstellen, die die Funktionalität von Always Encrypted mit Secure Enclaves auf einer SQL Server-Instanz verwendet, für die die Enclave nicht konfiguriert ist, wird der Wiederherstellungsvorgang erfolgreich durchgeführt, und alle Funktionen, die nicht auf die Enclave angewiesen sind, sind verfügbar. Alle nachfolgenden Abfragen, die die Enclave-Funktionalität verwenden, schlagen jedoch fehl, und Indizes auf Enclave-fähigen Spalten mit zufälliger Verschlüsselung werden ungültig. Dasselbe gilt, wenn Sie eine Datenbank mit Always Encrypted mit Secure Enclaves an die Instanz anfügen, für die die Enclave nicht konfiguriert ist.

Wenn Ihre Datenbank Indizes auf Enclave-fähigen Spalten mit zufälliger Verschlüsselung enthält, stellen Sie sicher, dass Sie die [Schnellere Datenbankwiederherstellung (ADR)](../../backup-restore/restore-and-recovery-overview-sql-server.md#adr) in der Datenbank aktivieren, bevor Sie eine Datenbanksicherung erstellen. Mit ADR wird sichergestellt, dass die Datenbank, einschließlich der Indizes, sofort nach der Wiederherstellung der Datenbank verfügbar ist. Weitere Informationen finden Sie unter [Datenbankwiederherstellung](#database-recovery).

Wenn Sie Ihre Datenbank mit einer BBACPAC-Datei migrieren, müssen Sie sicherstellen, dass Sie alle Indizes auf Enclave-fähige Spalten mit randomisierter Verschlüsselung löschen, bevor Sie die BACPAC-Datei erstellen.

## <a name="known-limitations"></a>Bekannte Einschränkungen
Always Encrypted mit Secure Enclaves adressiert einige Einschränkungen von Always Encrypted, indem die folgenden Vorgänge aktiviert werden:

- Direkte kryptografische Vorgänge.
- Musterabgleich (LIKE) und Vergleichsoperatoren für Spalten, die mithilfe der zufälligen Verschlüsselung verschlüsselt wurden.
    > [!NOTE]
    > Die obigen Vorgänge werden für Zeichenfolgenspalten unterstützt, die Sortierungen mit einer binary2-Sortierreihenfolge (BIN2-Sortierungen) verwenden. Zeichenfolgenspalten mit Nicht-BIN2-Sortierung können mit zufälliger Verschlüsselung und Enclave-fähigen Spaltenverschlüsselungsschlüsseln verschlüsselt werden. Die einzige neue Funktionalität, die für solche Spalten aktiviert ist, ist jedoch die dirkte Verschlüsselung.
- Erstellen von nicht gruppierten Indizes für Spalten mit zufälliger Verschlüsselung.

Alle anderen Einschränkungen für Always Encrypted, die unter den [Featuredetails](always-encrypted-database-engine.md#feature-details) aufgeführt sind, gelten auch für Always Encrypted mit Secure Enclaves.

Die folgenden Einschränkungen sind für Always Encrypted mit Secure Enclaves zu beachten:

- Gruppierte Indizes können nicht auf Enclave-fähigen Spalten mit zufälliger Verschlüsselung erstellt werden.
- Enclave-fähige Spalten mit zufälliger Verschlüsselung können keine Primärschlüsselspalten sein und können nicht durch Fremdschlüsselbeschränkungen oder eindeutige Schlüsselbeschränkungen referenziert werden.
- Nur Joins geschachtelter Schleifen (mit Indizes, falls verfügbar) werden für Enclave-fähige Spalten mit zufälliger Verschlüsselung unterstützt. Hashjoins und zusammengeführte Joins werden nicht unterstützt. 
- Direkte Verschlüsselungsvorgänge können nicht mit anderen Änderungen an Spaltenmetadaten kombiniert werden. Ausgenommen hiervon sind Änderungen einer Sortierung innerhalb derselben Codeseite und der NULL-Zulässigkeit. Beispiel: Sie können nicht in einer einzigen `ALTER TABLE`/`ALTER COLUMN`-Transact-SQL-Anweisung eine Spalte verschlüsseln, erneut verschlüsseln oder entschlüsseln UND den Datentyp der Spalte ändern. Sie müssen zwei separate Anweisungen verwenden.
- Die Verwendung von Enclave-fähigen Schlüsseln für Spalten in In-Memory-Tabellen wird nicht unterstützt.
- Ausdrücke, die berechnete Spalten definieren, können keine Berechnungen für enclave-fähige Spalten mit zufallsbasierter Verschlüsselung durchführen (auch wenn es sich bei den Berechnungen um LIKE- und Bereichsvergleiche handelt).
- Escapezeichen werden in Parametern des LIKE-Operators in Enclave-fähigen Spalten, die zufällige Verschlüsselung verwenden, nicht unterstützt.
- Abfragen mit dem LIKE-Operator oder einem Vergleichsoperator, der einen Abfrageparameter mit einem der folgenden Datentypen hat (die nach der Verschlüsselung zu großen Objekten werden), ignorieren Indizes und führen Tabellenscans durch.
    - `nchar[n]` und `nvarchar[n]`, wenn n größer als 3967 ist.
    - `char[n]`, `varchar[n]`, `binary[n]`, `varbinary[n]`, wenn n größer als 7935 ist.
- Tooleinschränkungen:
  - Die einzigen unterstützten Schlüsselspeicher für Enclave-fähige Spaltenhauptschlüssel sind Windows Certificate Store und Azure Key Vault.
  - Importieren/Exportieren von Datenbanken mit Enclave-fähigen Schlüsseln wird nicht unterstützt.
  - Um einen direkten kryptografischen Vorgang über eine `ALTER TABLE`/`ALTER COLUMN`-Anweisung auszulösen, müssen Sie die Anweisung über ein Abfragefenster in SSMS ausgeben. Alternativ dazu können Sie selbst ein Programm schreiben, das die Anweisung ausgibt. Das Cmdlet „Set-SqlColumnEncryption“ im SQL Server-PowerShell-Modul und der Always Encrypted-Assistent in SQL Server Management Studio unterstützen derzeit die direkte Verschlüsselung nicht. Beide Tools verschieben derzeit die Daten aus der Datenbank, um kryptografische Vorgänge auszuführen – auch dann, wenn die für die Vorgänge verwendeten Spaltenverschlüsselungsschlüssel Enclave-fähig sind.

## <a name="next-steps"></a>Nächste Schritte
- [Tutorial: Erste Schritte mit Always Encrypted mit Secure Enclaves mithilfe von SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md)
- [Konfigurieren und Verwenden von Always Encrypted mit Secure Enclaves](configure-always-encrypted-enclaves.md)

## <a name="see-also"></a>Weitere Informationen
- [Verwalten von Schlüsseln für Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-manage-keys.md)
- [Konfigurieren einer direkten Spaltenverschlüsselung mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-configure-encryption.md)
- [Abfragen von Spalten mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-query-columns.md)
- [Aktivieren von Always Encrypted mit Secure Enclaves für vorhandene verschlüsselte Spalten](always-encrypted-enclaves-enable-for-encrypted-columns.md)
- [Erstellen und Verwenden von Indizes in Spalten mithilfe von Always Encrypted mit Secure Enclaves](always-encrypted-enclaves-create-use-indexes.md)


