---
title: Anzeige 3 des Datenquellen-Assistenten (ODBC-Treiber für SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/27/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 63391969f378fdefbfa9547c079dcce4ff259e22
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67936546"
---
# <a name="data-source-wizard-screen-3"></a>Datenquellen-Assistent (Bildschirm 3)

Geben Sie die Standarddatenbank, verschiedene ANSI-Optionen, die vom Treiber verwendet werden sollen, und den Namen eines Spiegelservers an.

## <a name="options"></a>Tastatur

### <a name="change-the-default-database-to"></a>Standarddatenbank ändern in

Gibt den Namen der Standarddatenbank für jede mit dieser Datenquelle hergestellte Verbindung an. Wenn dieses Kästchen deaktiviert ist, verwenden Verbindungen die für die Anmelde-ID auf dem Server definierte Standarddatenbank. Wenn dieses Kästchen aktiviert ist, überschreibt die in dem Kästchen bezeichnete Datenbank die für die Anmelde-ID definierte Standarddatenbank. Wenn das Kästchen **Datenbank-Dateinamen anfügen** den Namen einer primären Datei hat, wird die durch die primäre Datei beschriebene Datenbank als Datenbank mithilfe des in dem Kästchen **Standarddatenbank ändern in** angegebenen Datenbanknamens angefügt.

Es ist effizienter, die Standarddatenbank für die Anmelde-ID zu verwenden, als eine Standarddatenbank in der ODBC-Datenquelle anzugeben.

### <a name="mirror-server"></a>Spiegelserver

Gibt den Namen des Failoverpartners der zu spiegelnden Datenbank an. Wenn ein Datenbankname in dem Feld **Die Standarddatenbank ändern auf** nicht angezeigt wird oder der angezeigte Name die Standarddatenbank ist, ist der **Spiegelserver** abgeblendet.

Optional können Sie einen Serverprinzipalnamen (SPN) für den Spiegelserver angeben. Der SPN für den Spiegelserver wird zur gegenseitigen Authentifizierung zwischen Client und Server verwendet.

### <a name="attach-database-filename"></a>Datenbank-Dateinamen anfügen

Gibt den Namen der primären Datei für eine anfügbare Datenbank an. Diese Datenbank wird angefügt und als Standarddatenbank für die Datenquelle verwendet. Geben Sie den vollständigen Pfad und den Dateinamen für die primäre Datei an. Der im Feld **Die Standarddatenbank ändern auf** angegebene Datenbankname wird als Name für die angefügte Datenbank verwendet.

### <a name="use-ansi-quoted-identifiers"></a>ANSI-Anführungszeichen verwenden

Gibt an, dass QUOTED_IDENTIFIERS auf ON festgelegt werden soll, wenn der ODBC Driver for SQL Server eine Verbindung herstellt. Wenn dieses Kontrollkästchen aktiviert wird, erzwingt SQL Server ANSI-Regeln für Anführungszeichen. Doppelte Anführungszeichen können nur für Bezeichner verwendet werden, z. B. Spalten- und Tabellennamen. Zeichenfolgen müssen in einfache Anführungszeichen eingeschlossen werden:

```
SELECT "LastName"
FROM "Person.Contact"
WHERE "LastName" = 'O''Brien'
```

Wenn dieses Kontrollkästchen deaktiviert wird, treten bei Anwendungen, die Bezeichner verwenden, wie z. B. das Abfragehilfsprogramm von Microsoft, das mit Microsoft Excel geliefert wird, Fehler beim Generieren von SQL-Anweisungen mit Bezeichnern in Anführungsstrichen auf.

### <a name="use-ansi-nulls-paddings-and-warnings"></a>ANSI-Nullen, -Auffüllungen und -Warnungen verwenden

Gibt an, dass die Optionen ANSI_NULLS, ANSI_WARNINGS und ANSI_PADDINGS auf ON festgelegt werden sollen, wenn der ODBC Driver for SQL Server eine Verbindung herstellt.

Wenn ANSI_NULLS auf ON festgelegt ist, erzwingt der Server ANSI-Regeln beim Vergleichen von Spalten für NULL. Die ANSI-Syntax „IS NULL“ oder „IS NOT NULL“ muss für alle NULL-Vergleiche verwendet werden. Die Transact-SQL-Syntax „= NULL“ wird nicht unterstützt.

Wenn ANSI_WARNINGS auf ON festgelegt sind, gibt SQL Server Warnmeldungen für Bedingungen aus, die gegen ANSI-Regeln, aber nicht gegen Regeln von Transact-SQL verstoßen. Beispiele für solche Fehler sind das Abschneiden von Daten bei der Ausführung einer INSERT- oder UPDATE-Anweisung oder das Stoßen auf einen Nullwert während einer Aggregatfunktion. 

Wenn ANSI_PADDING auf ON festgelegt ist, werden nachfolgende Leerzeichen nach **varchar**-Werten und nachfolgende Nullen nach **varbinary**-Werten nicht automatisch gekürzt.

### <a name="application-intent"></a>Anwendungsabsicht

Deklariert den Arbeitsauslastungstyp der Anwendung beim Herstellen einer Verbindung mit einem Server. Mögliche Werte sind **ReadOnly** und **ReadWrite**.

### <a name="multi-subnet-failover"></a>Multisubnetz-Failover.

Wenn Ihre Anwendung eine Verbindung mit einer hochverfügbaren Verfügbarkeitsgruppe für die Notfallwiederherstellung (Always On-Verfügbarkeitsgruppen) in einem anderen Subnetz herstellt, wird das **Multisubnetzfailover** aktiviert. konfiguriert den ODBC Driver for SQL Server, um eine schnellere Erkennung sowie die Verbindung zu dem (gerade) aktiven Server zu gewährleisten.

### <a name="transparent-network-ip-resolution"></a>Transparente Netzwerk-IP-Adressauflösung

Ändert das Verhalten des **Multisubnetzfailovers**, sodass eine schnellere Wiederherstellung der Verbindung beim Failover ermöglicht wird. Weitere Informationen finden Sie unter [Using Transparent Network IP Resolution (Verwenden der transparenten Netzwerk-IP-Adressauflösung)](../../../connect/odbc/using-transparent-network-ip-resolution.md).

### <a name="column-encryption"></a>Spaltenverschlüsselung

Aktiviert automatische Ent- und Verschlüsselung von Datenübertragungen zwischen mit dem [Always Encrypted](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)-Feature verschlüsselten Spalten (ab SQL Server 2016 verfügbar).

### <a name="use-fmtonly-metadata-discovery"></a>Verwenden der FMTONLY-Metadatenermittlung:

Verwenden Sie die alte SET FMTONLY-Methode zur Metadatenermittlung, wenn Sie eine Verbindung mit SQL Server 2012 oder höher herstellen. Aktivieren Sie diese Option nur, wenn die Verwendung von Abfragen nicht von [sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) unterstützt wird, z. B. wenn temporäre Tabellen enthalten sind. 

### <a name="next"></a>Next (Weiter)

Wechselt zum nächsten Bildschirm des Assistenten

### <a name="back"></a>Zurück

Kehrt zum vorherigen Bildschirm des Assistenten zurück

## <a name="next-steps"></a>Nächste Schritte

[Datenquellen-Assistent (Bildschirm 2)](../../../connect/odbc/windows/dsn-wizard-2.md)

[Datenquellen-Assistent (Bildschirm 4)](../../../connect/odbc/windows/dsn-wizard-4.md)
