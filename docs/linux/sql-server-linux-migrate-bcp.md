---
title: Massenkopieren von Daten mit SQL Server unter Linux | Microsoft-Dokumentation
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/30/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 7b93d0d7-7946-4b78-b33a-57d6307cdfa9
ms.openlocfilehash: bda200cccdaadb4db30b95289c2e16982a4e1f4b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66713135"
---
# <a name="bulk-copy-data-with-bcp-to-sql-server-on-linux"></a>Massenkopieren von Daten mit Bcp für den SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel wird gezeigt, wie Sie mit der [Bcp](../tools/bcp-utility.md) Befehlszeilen-Hilfsprogramm zum Massenkopieren von Daten zwischen einer Instanz von SQL Server unter Linux und einer Datendatei in eine vom Benutzer angegebenes Format.

Sie können `bcp` große Anzahl von Zeilen in SQL Server-Tabellen zu importieren oder Exportieren von Daten aus SQL Server-Tabellen in Datendateien. Außer in Verbindung mit der Option Queryout `bcp` erfordert keine Kenntnisse von Transact-SQL. Die `bcp` Befehlszeilen-Hilfsprogramm funktioniert nur mit Microsoft SQL Server lokal oder in der Cloud unter Linux, Windows oder Docker und Azure SQL-Datenbank und Azure SQL Data Warehouse.

In diesem Artikel lernen Sie Folgendes:
- Importieren von Daten in einer Tabelle mit den `bcp in` Befehl
- Exportieren von Daten aus einer Tabelle mit den `bcp out` Befehl

## <a name="install-the-sql-server-command-line-tools"></a>Installieren der SQL Server-Befehlszeilentools

`bcp` ist Teil der SQL Server-Befehlszeilentools, die mit SQL Server unter Linux nicht automatisch installiert werden. Wenn Sie die SQL Server-Befehlszeilentools auf Ihrem Linux-Computer noch nicht installiert haben, müssen Sie sie installieren. Wählen Sie für Weitere Informationen zum Installieren der Tools Ihrer Linux-Distribution, in der folgenden Liste:

- [Red Hat Enterprise Linux (RHEL)](sql-server-linux-setup-tools.md#RHEL)
- [Ubuntu](sql-server-linux-setup-tools.md#ubuntu)
- [SUSE Linux Enterprise Server (SLES)](sql-server-linux-setup-tools.md#SLES)

## <a name="import-data-with-bcp"></a>Importieren von Daten mit bcp

In diesem Tutorial erstellen Sie einer Beispieldatenbank und eine Tabelle in der lokalen SQL Server-Instanz ( **"localhost"** ) und dann `bcp` , in dem Beispiel für die Tabelle aus einer Textdatei auf dem Datenträger zu laden.

### <a name="create-a-sample-database-and-table"></a>Erstellen einer Beispieldatenbank und eine Tabelle

Wir erstellen zunächst eine Beispieldatenbank mit einer einfachen Tabelle, die im weiteren Verlauf in diesem Tutorial verwendet wird.

1. Öffnen Sie auf Ihrer Linux-Feld ein Befehl-Terminal ein.

2. Kopieren Sie die folgenden Befehle in der terminal-Fenster. Diese Befehle verwenden die **Sqlcmd** Befehlszeilen-Hilfsprogramm zum Erstellen einer Beispieldatenbank (**BcpSampleDB**) und eine Tabelle (**TestEmployees**) in der lokalen SQL Server-Instanz ( **"localhost"** ). Ersetzen Sie die `username` und `<your_password>` vor dem Ausführen der Befehle nach Bedarf.

Erstellen Sie die Datenbank **BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -Q "CREATE DATABASE BcpSampleDB;"
```
Erstellen Sie die Tabelle **TestEmployees** in der Datenbank **BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -d BcpSampleDB -Q "CREATE TABLE TestEmployees (Id INT IDENTITY(1,1) NOT NULL PRIMARY KEY, Name NVARCHAR(50), Location NVARCHAR(50));"
```
### <a name="create-the-source-data-file"></a>Erstellen Sie die Quelldatendatei
Kopieren Sie den folgenden Befehl in Ihrem Terminalfenster. Wir verwenden die integrierte `cat` Befehl zum Erstellen einer Datei mit Beispieldaten Text mit drei Datensätze speichern Sie die Datei in Ihrem Basisverzeichnis als **~/test_data.txt**. Die Felder in den Einträgen werden durch ein Komma getrennt.

```bash
cat > ~/test_data.txt << EOF
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
EOF
```

Sie können überprüfen, ob die Datendatei ordnungsgemäß erstellt wurde, indem Sie den folgenden Befehl in Ihrem Terminalfenster ausführen:
```bash 
cat ~/test_data.txt
```

Dies sollte Folgendes in Ihrem Terminalfenster angezeigt werden:
```bash
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

### <a name="import-data-from-the-source-data-file"></a>Importieren von Daten aus der Quelldatendatei
Kopieren Sie die folgenden Befehle in der terminal-Fenster. Dieser Befehl verwendet `bcp` für die Verbindung mit der lokalen SQL Server-Instanz ( **"localhost"** ) und importieren Sie die Daten aus der Datendatei ( **~/test_data.txt**) in die Tabelle (**TestEmployees** ) in der Datenbank (**BcpSampleDB**). Denken Sie daran, ersetzen Sie den Benutzernamen und `<your_password>` vor dem Ausführen der Befehle nach Bedarf.

```bash 
bcp TestEmployees in ~/test_data.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t  ','
```

Hier ist eine kurze Übersicht über die Befehlszeilenparameter und verwendet `bcp` in diesem Beispiel:
- `-S`: Gibt die Instanz von SQL Server für die Verbindung
- `-U`: Gibt die Anmelde-ID verwendet, um die Verbindung mit SQL Server
- `-P`: Gibt das Kennwort für die Anmelde-ID
- `-d`: Gibt die Datenbank für die Verbindung
- `-c`: führt Vorgänge, die mit einem Zeichendatentyp
- `-t`: Gibt das Feldabschlusszeichen. Wir verwenden `comma` als Feldabschlusszeichen für die Datensätze in unsere Datendatei

> [!NOTE]
> Geben wir kein benutzerdefiniertes Zeilenabschlusszeichen in diesem Beispiel an. Zeilen in der Textdatei für die Daten wurden mit ordnungsgemäß beendet `newline` , wenn es verwendet die `cat` Befehl aus, um die Datei zuvor zu erstellen.

Sie können überprüfen, ob die Daten erfolgreich importiert wurde, indem Sie den folgenden Befehl in Ihrem Terminalfenster ausführen. Ersetzen Sie die `username` und `<your_password>` vor Ausführung des Befehls nach Bedarf.
```bash 
sqlcmd -S localhost -d BcpSampleDB -U sa -P <your_password> -I -Q "SELECT * FROM TestEmployees;"
```

Dies sollte die folgenden Ergebnisse angezeigt werden:
```bash
Id          Name                Location
----------- ------------------- -------------------
          1 Jared               Australia
          2 Nikita              India
          3 Tom                 Germany

(3 rows affected)
```

## <a name="export-data-with-bcp"></a>Exportieren von Daten mit bcp

In diesem Tutorial verwenden Sie `bcp` zum Exportieren von Daten aus der Beispieltabelle, die wir zuvor erstellt haben, eine neue Datei.

Kopieren Sie die folgenden Befehle in der terminal-Fenster. Diese Befehle verwenden die `bcp` Befehlszeilen-Hilfsprogramm zum Exportieren von Daten aus der Tabelle **TestEmployees** in der Datenbank **BcpSampleDB** in eine neue Datendatei namens **~/test_export.txt** .  Denken Sie daran, ersetzen Sie den Benutzernamen und `<your_password>` vor Ausführung des Befehls nach Bedarf.

```bash 
bcp TestEmployees out ~/test_export.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t ','
```

Sie können überprüfen, ob die Daten ordnungsgemäß exportiert wurde, indem Sie den folgenden Befehl in Ihrem Terminalfenster ausführen:
```bash 
cat ~/test_export.txt
```

Dies sollte Folgendes in Ihrem Terminalfenster angezeigt werden:
```
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

## <a name="see-also"></a>Siehe auch
- [bcp (Hilfsprogramm)](../tools/bcp-utility.md)
- [Datenformate für die Kompatibilität bei Verwendung von bcp](../relational-databases/import-export/specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)
- [Importieren von Massendaten mithilfe von BULK INSERT](../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)
- [BULK INSERT (Transact-SQL)](../t-sql/statements/bulk-insert-transact-sql.md)
