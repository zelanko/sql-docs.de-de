---
title: Konfigurieren von SSIS unter Linux mit Ssis-Conf | Microsoft-Dokumentation
description: Dieser Artikel beschreibt das Konfigurieren von SQL Server Integration Services (SSIS) unter Linux mit dem Ssis-Conf-Hilfsprogramm.
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 957333697112105799d29aebecc3b3fcb049eb99
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764968"
---
# <a name="configure-sql-server-integration-services-on-linux-with-ssis-conf"></a>Konfigurieren von SQL Server Integration Services unter Linux mit Ssis-conf

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Sie führen die `ssis-conf` Konfigurationsskript, bei der Installation von SQL Server Integration Services (SSIS) für Red Hat Enterprise Linux und Ubuntu. Weitere Informationen zum Installieren von SSIS finden Sie unter [installieren Sie SQL Server Integration Services (SSIS) für Linux](sql-server-linux-setup-ssis.md).

Sie können auch die `ssis-conf` Hilfsprogramm so konfigurieren Sie die folgenden Eigenschaften:

| Befehl | Description |
|-------------|---------------------------------------------------------------------|
| Set-edition | Legen Sie die Edition von SQL Server                                       |
| Telemetrie   | Aktivieren oder Deaktivieren von SQL Server Integration Services-telemetriedienst |
| Setup       | Initialisieren und Einrichten von Microsoft SQL Server Integration Services      |
|||

## <a name="run-ssis-conf"></a>Ausführen von Ssis-conf

In den Beispielen in diesem Artikel ausführen `ssis-conf` durch den vollständigen Pfad angeben: `/opt/ssis/bin/ssis-conf`. Wenn Sie zu diesem Speicherort navigieren, vor dem Ausführen von `ssis-conf`, führen Sie das Hilfsprogramm im Kontext des aktuellen Verzeichnisses: `./ssis-conf`.

Achten Sie darauf, dass die Befehle, die beschrieben werden in diesem Artikel mit Stammberechtigungen ausgeführt. Führen Sie z. B. `sudo /opt/ssis/bin/ssis-conf setup` und nicht `/opt/ssis/bin/ssis-conf setup`.

Führen Sie diese Befehle mit den Anweisungen in der Sprache, die Sie bevorzugen, können Sie kein Gebietsschema angeben. Z. B. um aufforderungen auf Chinesisch zu erhalten, führen Sie den folgenden Befehl: `sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="use-set-edition-to-set-the-edition-of-sql-server-integration-services"></a>Verwenden Sie Set-Edition, legen Sie die Edition von SQL Server Integration Services

Die Edition von SSIS wird mit der Edition von SQL Server ausgerichtet.

Geben Sie den folgenden Befehl: `$ sudo /opt/ssis/bin/ssis-conf set-edition`.

Nachdem Sie den Befehl eingegeben haben, erhalten Sie die folgende Aufforderung:

```
Choose an edition of SQL Server:

1) Evaluation (free, no production use rights, 180-day limit)

2) Developer (free, no production use rights)

3) Express (free)

4) Web (PAID)

5) Standard (PAID)

6) Enterprise (PAID)

7) Enterprise Core (PAID)

8) I bought a license through a retail sales channel and have a product key to enter.

Details about editions can be found at https://go.microsoft.com/fwlink/?LinkId=852748&clcid=0x409.

Use of PAID editions of this software requires separate licensing through a Microsoft Volume Licensing program.

By choosing a PAID edition, you are verifying that you have the appropriate number of licenses in place to install and run this software.

Enter your edition (1-8):
```

Wenn Sie einen Wert von 1 bis 7 eingeben, wird das System eine kostenlose oder KOSTENPFLICHTIGE Edition konfiguriert. Wenn Sie auf "8" eingeben, fordert das Dienstprogramm Sie den Product Key eingeben, den Sie erworben haben:

```
Enter the 25-character product key:
```

## <a name="use-telemetry-to-configure-customer-feedback"></a>Verwenden Sie Telemetriedaten, um Feedback von Kunden zu konfigurieren.

Die `telemetry` Befehl ermittelt, ob SSIS Feedback an Microsoft sendet.

Für kostenlose Editionen (d.h., Express, Developer und Evaluation-Editionen) wird der telemetriedienst ist immer aktiviert. Wenn Sie eine kostenlose Edition haben, können keine der `telemetry` Befehl zum Deaktivieren der Telemetrie.

Geben Sie den folgenden Befehl: `$ sudo /opt/ssis/bin/ssis-conf telemetry`.

Für KOSTENPFLICHTIGEN Editionen Nachdem Sie den Befehl aus, geben Sie erhalten die folgende Aufforderung Sie:

```
Send feature usage data to Microsoft. Feature usage data includes information about your hardware configuration and how you use SQL Server Integration Services.

[Yes/No]:
```

Bei Auswahl von **Ja**, die telemetriedienst aktiviert ist und gestartet wird. Der Dienst wird automatisch nach jedem Startvorgang gestartet. Bei Auswahl von **keine**, der telemetriedienst beendet und ist deaktiviert.

## <a name="use-setup-to-initialize-and-set-up-microsoft-sql-server-integration-services"></a>Mithilfe von Setup initialisieren und Einrichten von Microsoft SQL Server Integration Services

Verwenden der `setup` Befehl jedes Mal, wenn Sie SSIS installieren.

Geben Sie den folgenden Befehl: `sudo /opt/ssis/bin/ssis-conf setup`.

Das Hilfsprogramm fordert Ihre bestätigen oder geben Sie Werte für die folgenden Elemente:
-   Produkt-Lizenz
-   Lizenzbedingungen
-   Der telemetriedienst
-   Die von Integration Services verwendete Sprache

Zum Ausführen der `setup` Befehl mit den Anweisungen in der Sprache, mit dem Sie es vorziehen, können Sie ein Gebietsschema angeben. Z. B. um aufforderungen auf Chinesisch zu erhalten, führen Sie den folgenden Befehl: `sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="ssisconf-format"></a>SSIS.conf-format

Die folgenden `/var/opt/ssis/ssis.conf` Datei enthält ein Beispiel für jede Einstellung.

Für SQL Server können Sie Systemeinstellungen ändern, indem Sie das Ändern der Werte in der `mssql.conf` Datei. Für SSIS Sie *kann nicht* Systemeinstellungen ändern, indem Sie das Ändern der Werte in der `ssis.conf` Datei. Die `ssis.conf` Datei zeigt nur die Ergebnisse des Setups. Wenn Sie die Einstellungen für SSIS ändern möchten, können Sie löschen die `ssis.conf` , und führen Sie die `setup` -Befehl erneut aus.

Hier ist ein Beispiel `ssis.conf` Datei. Jedes Feld entspricht das Ergebnis eines Setup-Schritts.

```
[LICENSE]
                       
registered = Y        
                       
pid = enterprisecore  
                       
[EULA]
                       
accepteula = Y        
                       
[TELEMETRY]
                       
enabled = Y           
                       
[language]
                       
lcid = 2052
```

## <a name="related-content-about-ssis-on-linux"></a>Verwandte Inhalte zu SSIS unter Linux
-   [Extrahieren, Transformieren und Laden von Daten unter Linux mit SSIS](sql-server-linux-migrate-ssis.md)
-   [Installieren von SQL Server Integration Services (SSIS) unter Linux](sql-server-linux-setup-ssis.md)
-   [Einschränkungen und bekannte Probleme für SSIS unter Linux](sql-server-linux-ssis-known-issues.md)
-   [Zeitplan SQL Server Integration Services-paketausführung unter Linux mit cron](sql-server-linux-schedule-ssis-packages.md)
