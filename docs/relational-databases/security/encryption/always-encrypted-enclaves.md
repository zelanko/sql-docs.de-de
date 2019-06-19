---
title: Always Encrypted mit Secure Enclaves (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 377c2d95564e7348bdfb5de9480c7c7f5004c7f7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65938159"
---
# <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted mit Secure Enclaves
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]


Always Encrypted mit Secure Enclaves bietet zusätzliche Funktionalität für das Feature [Always Encrypted](always-encrypted-database-engine.md).

Always Encrypted wurde in SQL Server 2016 eingeführt und schützt vertrauliche Daten vor Schadsoftware und dem Zugriff *nicht autorisierter* SQL Server-Benutzer mit hohen Berechtigungen. Nicht autorisierte Benutzer mit hohen Berechtigungen sind Datenbankadministratoren, Computeradministratoren, Cloudadministratoren sowie alle anderen Benutzer, die legitim auf Serverinstanzen, Hardware und ähnliches zugreifen, aber keine Zugriff auf einige oder alle der tatsächlichen Daten haben sollten. 

Bisher schützte Always Encrypted die Daten, indem das Feature die Daten auf Clientseite verschlüsselte und niemals zuließ, dass die Daten oder die zugehörigen kryptografischen Schlüssel als Klartext in der SQL Server-Engine angezeigt wurden. Daher war die Funktionalität von verschlüsselten Spalten innerhalb der Daten stark eingeschränkt. Die einzigen Vorgänge, die SQL Server für verschlüsselte Daten ausführen konnte, waren Gleichheitsvergleiche (und diese waren nur bei deterministischer Verschlüsselung verfügbar). Alle anderen Vorgänge, beispielweise kryptografische Vorgänge (anfängliche Datenverschlüsselung oder Schlüsselrotation), sowie umfangreiche Berechnungen (z.B. Musterabgleich) wurden innerhalb der Datenbank nicht unterstützt. Benutzer mussten die Daten aus der Datenbank verschieben, um diese Vorgänge auf Clientseite auszuführen.

Always Encrypted *mit Secure Enclaves* beseitigt diese Einschränkungen, indem Berechnungen für Klartextdaten innerhalb einer Secure Enclave auf Serverseite zugelassen werden. Eine Secure Enclave ist eine geschützte Arbeitsspeicherregion im SQL Server-Prozess und fungiert als vertrauenswürdige Ausführungsumgebung für die Verarbeitung vertraulicher Daten in der SQL Server-Engine. Eine Secure Enclave wird dem Rest von SQL Server und anderen Prozessen auf dem Hostcomputer als Blackbox angezeigt. Es gibt keine Möglichkeit, Daten oder Code innerhalb der Enclave von außen anzuzeigen, auch nicht mit einem Debugger.  


Always Encrypted verwendet Secure Enclaves wie im folgenden Diagramm veranschaulicht:

![Datenfluss](./media/always-encrypted-enclaves/ae-data-flow.png)



Beim Analysieren der Abfrage einer Anwendung ermittelt die SQL Server-Engine, ob die Abfrage Vorgänge für verschlüsselte Daten enthält, für die die Verwendung der Secure Enclave erforderlich ist. Bei Abfragen, für die auf die Secure Enclave zugegriffen werden muss, gilt Folgendes:

- Der Clienttreiber sendet die für die Vorgänge erforderlichen Spaltenverschlüsselungsschlüssel an die Secure Enclave (oder einen sicheren Kanal). 
- Dann übermittelt der Clienttreiber die Abfrage zusammen mit den verschlüsselten Abfrageparametern zur Ausführung.

Während der Verarbeitung der Abfrage werden weder die Daten noch die Spaltenverschlüsselungsschlüssel außerhalb der Secure Enclave als Klartext in der SQL Server-Engine verfügbar gemacht. Die SQL Server-Engine delegiert kryptografische Vorgänge und Berechnungen für verschlüsselte Spalten an die Secure Enclave. Bei Bedarf entschlüsselt die Secure Enclave die Abfrageparameter und/oder die in verschlüsselten Spalten gespeicherten Daten und führt die angeforderten Vorgänge aus.

## <a name="why-use-always-encrypted-with-secure-enclaves"></a>Was spricht für die Verwendung von Always Encrypted mit Secure Enclaves?

Mit Secure Enclaves schützt Always Encrypted die Vertraulichkeit von Daten und bietet gleichzeitig folgende Vorteile:

- **Direkte Verschlüsselung**: Kryptografische Vorgänge für vertrauliche Daten, wie z.B. die anfängliche Datenverschlüsselung oder das Rotieren eines Spaltenverschlüsselungsschlüssels, werden innerhalb der Secure Enclave ausgeführt und erfordern kein Verschieben der Daten an einen Ort außerhalb der Datenbank. Sie können die direkte Verschlüsselung mit der Transact-SQL-Anweisung ALTER TABLE ausführen. Sie benötigen keine Tools wie etwa den Always Encrypted-Assistenten in SSMS oder das PowerShell-Cmdlet „Set-SqlColumnEncryption“.

- **Umfangreiche Berechnungen (Vorschau)** : Vorgänge in verschlüsselten Spalten, wie z.B. Musterabgleich (das LIKE-Prädikat) und Bereichsvergleiche, werden innerhalb der Secure Enclave unterstützt. Damit lässt sich Always Encrypted für eine Vielzahl von Anwendungen und Szenarien verwenden, bei denen solche Berechnungen innerhalb des Datenbanksystems ausgeführt werden müssen.

> [!IMPORTANT]
> In [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] stehen für umfangreiche Berechnungen noch einige Leistungsoptimierungen aus. Zudem weisen solche Berechnungen eine eingeschränkte Funktionalität auf (z.B. keine Indizierung) und sind derzeit standardmäßig deaktiviert. Informationen zum Aktivieren umfangreicher Berechnungen finden Sie unter [Aktivieren von umfangreichen Berechnungen](configure-always-encrypted-enclaves.md#configure-a-secure-enclave).

In [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] verwendet Always Encrypted über [Virtualisierungsbasierte Sicherheit (VBS)](https://www.microsoft.com/security/blog/2018/06/05/virtualization-based-security-vbs-memory-enclaves-data-protection-through-isolation/) abgesicherte Secure Enclaves (auch als VSM-Enclaves bezeichnet) im Windows-Arbeitsspeicher.

## <a name="secure-enclave-attestation"></a>Nachweis von Secure Enclaves

Die Secure Enclave in der SQL Server-Engine kann im Klartextformat auf vertrauliche Daten, die in verschlüsselten Datenbankspalten gespeichert sind, sowie auf die entsprechenden Spaltenverschlüsselungsschlüssel zugreifen. Bevor eine Abfrage mit Enclave-Berechnungen an SQL Server übermittelt wird, muss der Clienttreiber innerhalb der Anwendung überprüfen, ob es sich bei der Secure Enclave um eine echte Enclave handelt, die auf einer bestimmten Technologie basiert (z.B. VBS). Darüber hinaus muss der Treiber überprüfen, ob der Code, der in der Enclave ausgeführt wird, für die Ausführung in der Enclave signiert wurde. 

Der Prozess der Überprüfung der Enclave wird als **Enclave-Nachweis** bezeichnet und erfordert in der Regel, dass ein Clienttreiber innerhalb der Anwendung (und manchmal auch SQL Server) einen externen Nachweisdienst kontaktiert. Die genauen Merkmale des Nachweisprozesses richten sich nach der Enclave-Technologie und dem Nachweisdienst.

Der Nachweisprozess, den SQL Server für Secure Enclaves für VBS in [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] unterstützt, ist der Windows Defender System Guard-Runtimenachweis, bei dem Host Guardian Service (HGS) als Nachweisdienst verwendet wird. Sie müssen HGS in Ihrer Umgebung konfigurieren und den Computer, auf dem Ihre SQL Server-Instanz gehostet wird, in HGS registrieren. Sie müssen auch Ihre Clientanwendungen oder -tools (z.B. SQL Server Management Studio) mit einem HGS-Nachweis konfigurieren.

## <a name="secure-enclave-providers"></a>Anbieter von Secure Enclaves

Um Always Encrypted mit Secure Enclaves verwenden zu können, muss eine Anwendung einen Clienttreiber nutzen, der dieses Feature unterstützt. In [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] müssen Ihre Anwendungen .NET Framework 4.7.2 und den .NET Framework-Datenanbieter für SQL Server verwenden. Darüber hinaus müssen .NET-Anwendungen mit einem **Anbieter für Secure Enclaves** konfiguriert werden, der genau auf den von Ihnen verwendeten Enclave-Typ (z.B. VBS) und Nachweisdienst (z.B. HGS) ausgerichtet ist. Die unterstützten Enclave-Anbieter werden separat in einem NuGet-Paket ausgeliefert, das Sie in Ihre Anwendung integrieren müssen. Ein Enclave-Anbieter implementiert die clientseitige Logik für das Nachweisprotokoll und für die Einrichtung eines sicheren Kanals mit einer Secure Enclave eines bestimmten Typs.

## <a name="enclave-enabled-keys"></a>Enclave-fähige Schlüssel

Always Encrypted mit Secure Enclave führt das Konzept der Enclave-fähigen Schlüssel ein:

- **Enclave-fähiger Spaltenhauptschlüssel**: Ein Spaltenhauptschlüssel, für den die ENCLAVE_COMPUTATIONS-Eigenschaft im Spaltenhauptschlüssel-Metadatenobjekt in der Datenbank angegeben ist. Das Spaltenhauptschlüssel-Metadatenobjekt muss auch eine gültige Signatur der Metadateneigenschaften enthalten.
- **Enclave-fähiger Spaltenverschlüsselungsschlüssel**: Ein Spaltenverschlüsselungsschlüssel, der mit einem Enclave-fähigen Spaltenhauptschlüssel verschlüsselt ist.

Wenn die SQL Server-Engine feststellt, dass die in einer Abfrage angegebenen Vorgänge innerhalb der Secure Enclave ausgeführt werden müssen, fordert die Engine den Clienttreiber auf, die für die Berechnungen erforderlichen Spaltenverschlüsselungsschlüssel für die Secure Enclave freizugeben. Der Clienttreiber gibt die Spaltenverschlüsselungsschlüssel nur dann frei, wenn diese Enclave-fähig sind (also mit Enclave-fähigen Spaltenhauptschlüsseln verschlüsselt wurden) und ordnungsgemäß signiert wurden. Andernfalls kann die Abfrage nicht ausgeführt werden.

## <a name="enclave-enabled-columns"></a>Enclave-fähige Spalten

Eine Enclave-fähige Spalte ist eine Datenbankspalte, die mit einem Enclave-fähigen Spaltenverschlüsselungsschlüssel verschlüsselt ist. Welche Funktionalität für eine Enclave-fähige Spalte verfügbar ist, richtet sich nach dem von der Spalte verwendeten Verschlüsselungstyp.

- **Deterministische Verschlüsselung**: Enclave-fähige Spalten, die die deterministische Verschlüsselung verwenden, unterstützen die direkte Verschlüsselung, aber keine anderen Vorgänge innerhalb der Secure Enclave. Gleichheitsvergleiche werden unterstützt, aber außerhalb der Enclave ausgeführt, indem der Chiffretext (außerhalb der Enclave) verglichen wird.  
- **Verschlüsselung nach dem Zufallsprinzip**: Enclave-fähige Spalten, die die Verschlüsselung nach dem Zufallsprinzip verwenden, unterstützen die direkte Verschlüsselung sowie umfangreiche Berechnungen innerhalb der Secure Enclave. Zu den unterstützten umfangreichen Berechnungen zählen Musterabgleich und [Vergleichsoperatoren](https://docs.microsoft.com/sql/t-sql/language-elements/comparison-operators-transact-sql), einschließlich Gleichheitsvergleich.

Weitere Informationen zu Verschlüsselungstypen finden Sie unter [Always Encrypted-Kryptografie](always-encrypted-cryptography.md).

Die folgende Tabelle fasst die für verschlüsselte Spalten verfügbaren Funktionen zusammen – je nachdem, ob die Spalten Enclave-fähige Spaltenverschlüsselungsschlüssel und einen Verschlüsselungstyp verwenden.

| **Vorgang**| **Spalte ist NICHT Enclave-fähig** |**Spalte ist NICHT Enclave-fähig**| **Spalte ist Enclave-fähig**  |**Spalte ist Enclave-fähig** |
|:---|:---|:---|:---|:---|
| | **Verschlüsselung nach dem Zufallsprinzip**  | **Deterministische Verschlüsselung**     | **Verschlüsselung nach dem Zufallsprinzip**      | **Deterministische Verschlüsselung**     |
| **Direkte Verschlüsselung** | Nicht unterstützt  | Nicht unterstützt   | Supported         | Supported    |
| **Gleichheitsvergleich**   | Nicht unterstützt | Außerhalb der Enclave unterstützt | Unterstützt (innerhalb der Enclave) | Außerhalb der Enclave unterstützt |
| **Vergleichsoperatoren zusätzlich zum Gleichheitsvergleich** | Nicht unterstützt  | Nicht unterstützt   | Supported      | Nicht unterstützt     |
| **LIKE**    | Nicht unterstützt      | Nicht unterstützt    | Supported     | Nicht unterstützt    |

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

## <a name="known-limitations"></a>Bekannte Einschränkungen

Allgemeine Einschränkungen: 

- Alle Einschränkungen, die unter [Details zur Funktion](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#feature-details) für die aktuelle Version von Always Encrypted aufgeführt sind, gelten auch für Always Encrypted mit Secure Enclaves (für Spalten, die mit Enclave-fähigen Schlüsseln verschlüsselt sind). Ausgenommen sind die Einschränkungen, die durch Hinzufügen der Unterstützung für direkte Verschlüsselung und umfangreiche Berechnungen aufgehoben werden.

- Der Gleichheitsvergleich bleibt der einzige Transact-SQL-Vorgang, der mit deterministischer Verschlüsselung unterstützt wird. Gleichheitsvergleiche erfolgen durch Vergleichen von Chiffretextwerten außerhalb der Enclave, unabhängig davon, ob die Verschlüsselungsschlüssel der Spalten Enclave-fähig sind oder nicht. Die einzige neue Funktionalität, die durch Enclave-fähige Spaltenverschlüsselungsschlüssel für die deterministische Verschlüsselung aktiviert wird, sind direkte kryptografische Vorgänge. Wenn Sie über eine Spalte verfügen, die mit deterministischer Verschlüsselung verschlüsselt ist (und über einen Schlüssel, der nicht Enclave-fähig ist), müssen Sie die Spalte mit der Verschlüsselung nach dem Zufallsprinzip neu verschlüsseln, um umfangreiche Berechnungen (Musterabgleich, Vergleichsoperationen) zu ermöglichen.

- Die vorhandenen Einschränkungen in Bezug auf Sortierungen gelten auch für Spalten, die mit Enclave-fähigen Spaltenverschlüsselungsschlüsseln verschlüsselt sind: Mit deterministischer Verschlüsselung verschlüsselte Zeichenfolgenspalten (char, nchar, varchar, nvarchar) müssen Sortierungen mit einer binary2-Sortierreihenfolge (BIN2-Sortierungen) verwenden. Zeichenfolgenspalten, die Nicht-BIN2-Sortierungen verwenden, können mit der Verschlüsselung nach dem Zufallsprinzip verschlüsselt werden. Die einzige neue Funktionalität, die für solche Spalten aktiviert wird (wenn sie mit Enclave-fähigen Spaltenverschlüsselungsschlüsseln verschlüsselt sind), ist die direkte Verschlüsselung. **Um umfangreiche Berechnungen (Musterabgleich, Vergleichsoperationen) zu unterstützen, muss eine Spalte eine BIN2-Sortierung verwenden** (und die Spalte muss mit Verschlüsselung nach dem Zufallsprinzip und einem Enclave-fähigen Spaltenverschlüsselungsschlüssel verschlüsselt sein).

- Die Verwendung von Enclave-fähigen Schlüsseln für Spalten in In-Memory-Tabellen wird nicht unterstützt.

- Direkte Verschlüsselungsvorgänge können nicht mit anderen Änderungen an Spaltenmetadaten kombiniert werden. Ausgenommen hiervon sind Änderungen der Sortierung und der NULL-Zulässigkeit. Beispiel: Sie können nicht in einer einzigen ALTER TABLE- oder ALTER COLUMN-Transact-SQL-Anweisung eine Spalte verschlüsseln, erneut verschlüsseln oder entschlüsseln UND den Datentyp der Spalte ändern. Sie müssen zwei separate Anweisungen verwenden.

Die folgenden Einschränkungen gelten für die aktuelle Vorschau, eine Lösung ist jedoch geplant:

- Enclave-fähige Spalten mit Verschlüsselung nach dem Zufallsprinzip können nicht indiziert werden. Das bedeutet, dass für Vergleichs- oder LIKE-Vorgänge Tabellenscans erforderlich sind.

- Der einzige Clienttreiber, der Always Encrypted mit Secure Enclaves unterstützt, ist der .NET Framework-Datenanbieter für SQL Server (ADO.NET) in .NET Framework 4.7.2. Es gibt keine Unterstützung für ODBC/JDBC.

- Die einzigen unterstützten Schlüsselspeicher für Enclave-fähige Spaltenhauptschlüssel sind Windows Certificate Store und Azure Key Vault.

- Die Toolunterstützung für Always Encrypted mit Secure Enclaves ist zurzeit unvollständig. Um einen direkten kryptografischen Vorgang über eine ALTER TABLE-Transact-SQL-Anweisung auszulösen, müssen Sie die Anweisung über ein Abfragefenster in SSMS ausgeben. Alternativ dazu können Sie selbst ein Programm schreiben, das die Anweisung ausgibt. Das Cmdlet „Set-SqlColumnEncryption“ im SQL Server-PowerShell-Modul und der Always Encrypted-Assistent in SQL Server Management Studio unterstützen die direkte Verschlüsselung noch nicht. Beide Tools verschieben derzeit die Daten aus der Datenbank, um kryptografische Vorgänge auszuführen – auch dann, wenn die für die Vorgänge verwendeten Spaltenverschlüsselungsschlüssel Enclave-fähig sind. 

## <a name="known-issues"></a>Bekannte Probleme

- Für umfangreiche Berechnungen für Nicht-Unicode-Zeichenfolgenspalten (char, varchar) muss eine BIN2-Sortierung auf Datenbankebene festgelegt werden. Weitere Informationen finden Sie bei den besonderen Überlegungen für Nicht-Unicode-Zeichenfolgenspalten unter [Verwalten von Sortierungen](configure-always-encrypted-enclaves.md#manage-collations).

## <a name="next-steps"></a>Next Steps

- Informationen zum Einrichten Ihrer Testumgebung mit anschließendem Testen der Funktionalität von Always Encrypted mit Secure Enclaves in SSMS finden Sie unter [Tutorial: Erste Schritte mit Always Encrypted mit Secure Enclaves mithilfe von SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md).
