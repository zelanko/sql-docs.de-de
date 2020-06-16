---
title: Emulieren von Oracle-Paketvariablen
description: Beschreibt, wie in SQL Server Migration Assistant (SSMA) Oracle-Paket Variablen in SQL Server emuliert werden.
author: nahk-ivanov
ms.prod: sql
ms.technology: ssma
ms.devlang: sql
ms.topic: article
ms.date: 1/22/2020
ms.author: alexiva
ms.openlocfilehash: ab7de81e16d1324aabd5f07421c1db4c51b3cf7c
ms.sourcegitcommit: e572f1642f588b8c4c75bc9ea6adf4ccd48a353b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2020
ms.locfileid: "84779462"
---
# <a name="emulating-oracle-package-variables"></a>Emulieren von Oracle-Paketvariablen

Oracle unterstützt das Kapseln von Variablen, Typen, gespeicherten Prozeduren und Funktionen in einem Paket. Beim Konvertieren von Oracle-Paketen müssen Sie Folgendes konvertieren:

* Prozeduren und Funktionen (öffentlich und privat)
* Variables
* Cursor
* Initialisierungs Routinen

In diesem Artikel wird beschrieben, wie SQL Server Migration Assistant (SSMA) für Oracle Paket Variablen in SQL Server konvertiert.

## <a name="conversion-basics"></a>Grundlagen der Konvertierung

SSMA für Oracle verwendet gespeicherte Prozeduren, die sich in einem speziellen `ssma_oracle` Schema zusammen mit Table befinden, um Paket Variablen zu speichern `ssma_oracle.db_storage` . Diese Tabelle wird nach `SPID` (Sitzungs Bezeichner) und Anmeldezeit gefiltert. Diese Filterung ermöglicht es Ihnen, zwischen Variablen unterschiedlicher Sitzungen zu unterscheiden.

Am Anfang der einzelnen konvertierten Paket Prozeduren wird von SSMA ein Rückruf für die `ssma_oracle.db_check_init_package` spezielle Prozedur durchgeführt, mit der überprüft wird, ob das Paket initialisiert ist, und bei Bedarf initialisiert wird. Jede Initialisierungs Prozedur bereinigt die Speicher Tabelle und legt die Standardwerte für jede Paket Variable fest.

## <a name="example"></a>Beispiel

Beachten Sie das folgende Beispiel zum umrechnen mehrerer Paket Variablen:

```sql
CREATE OR REPLACE PACKAGE MY_PACKAGE
IS
    space varchar(1) := ' ';
    unitname varchar(128) := 'My Simple Package';
    ts date := sysdate;
END;
```

Der SSMA konvertiert ihn in den folgenden Transact-SQL-Code:

```sql
CREATE PROCEDURE dbo.MY_PACKAGE$SSMA_Initialize_Package
AS
BEGIN
    EXECUTE ssma_oracle.db_clean_storage

    EXECUTE ssma_oracle.set_pv_varchar
        DB_NAME(),
        'DBO',
        'MY_PACKAGE',
        'SPACE',
        ' '

    EXECUTE ssma_oracle.set_pv_varchar
        DB_NAME(),
        'DBO',
        'MY_PACKAGE',
        'UNITNAME',
        'My Simple Package'

    DECLARE
        @temp datetime2

    SET @temp = sysdatetime()

    EXECUTE sysdb.ssma_oracle.set_pv_datetime2
      DB_NAME(),
      'DBO',
      'MY_PACKAGE',
      'TS',
      @temp
END
```

## <a name="emulating-get-and-set-methods-for-package-variables"></a>Emuinieren von Get-und Set-Methoden für Paket Variablen

Oracle verwendet `Get` `Set` die-Methode und die-Methode für die Paket Variablen, um zu verhindern, dass andere Unterprogramme Sie direkt lesen und schreiben. Wenn eine Anforderung besteht, einige Variablen zwischen den Aufrufen von Teilprogrammen in derselben Sitzung verfügbar zu halten, werden diese Variablen wie globale Variablen behandelt.

Um diese Bereichs Regel zu umgehen, verwendet SSMA für Oracle gespeicherte Prozeduren wie `ssma_oracle.set_pv_varchar` für jeden Variablentyp. Für den Zugriff auf diese Variablen verwendet SSMA eine Reihe von Transaktions unabhängigen `get_*` und- `set_*` Prozeduren und-Funktionen.

| Datentyp in Oracle | SSMA- `Set` Prozedur           |
| ------------------- | ------------------------------ |
| VARCHAR             | `ssma_oracle.set_pv_varchar`   |
| DATE                | `ssma_oracle.set_pv_datetime2` |
| CHAR                | `ssma_oracle.set_pv_varchar`   |
| INT                 | `ssma_oracle.set_pv_float`     |
| GLEITKOMMAZAHL               | `ssma_oracle.set_pv_float`     |

Um zwischen Variablen aus unterschiedlichen Sitzungen zu unterscheiden, speichert SSMA die Variablen zusammen mit Ihrem `SPID` (Sitzungs Bezeichner) und der Anmeldezeit der Sitzung. Folglich `get_*` behalten die-und- `set_*` Prozeduren die Variablen unabhängig von den Sitzungen, die Sie ausführen.
