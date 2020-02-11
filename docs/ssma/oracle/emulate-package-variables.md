---
title: Emulieren von Oracle-Paketvariablen
description: Beschreibt, wie in SQL Server Migration Assistant (SSMA) Oracle-Paket Variablen in SQL Server emuliert werden.
authors: nahk-ivanov
ms.service: ssma
ms.devlang: sql
ms.topic: article
ms.date: 1/22/2020
ms.author: alexiva
ms.openlocfilehash: 9a8ca5c7dfdda98e1c005c3851d061957cf67449
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "76762824"
---
# <a name="emulating-oracle-package-variables"></a>Emulieren von Oracle-Paketvariablen

Oracle unterstützt das Kapseln von Variablen, Typen, gespeicherten Prozeduren und Funktionen in einem Paket. Beim Konvertieren von Oracle-Paketen müssen Sie Folgendes konvertieren:

* Prozeduren und Funktionen (öffentlich und privat)
* Variables
* Cursor
* Initialisierungs Routinen

In diesem Artikel wird beschrieben, wie SQL Server Migration Assistant (SSMA) für Oracle Paket Variablen in SQL Server konvertiert.

## <a name="conversion-basics"></a>Grundlagen der Konvertierung

SSMA für Oracle verwendet gespeicherte Prozeduren, die sich in einem speziellen `ssma_oracle` Schema zusammen mit `ssma_oracle.db_storage` Table befinden, um Paket Variablen zu speichern. Diese Tabelle wird nach `SPID` (Sitzungs Bezeichner) und Anmeldezeit gefiltert. Diese Filterung ermöglicht es Ihnen, zwischen Variablen unterschiedlicher Sitzungen zu unterscheiden.

Am Anfang der einzelnen konvertierten Paket Prozeduren wird von SSMA ein `ssma_oracle.db_check_init_package` Rückruf für die spezielle Prozedur durchgeführt, mit der überprüft wird, ob das Paket initialisiert ist, und bei Bedarf initialisiert wird. Jede Initialisierungs Prozedur bereinigt die Speicher Tabelle und legt die Standardwerte für jede Paket Variable fest.

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

Oracle verwendet `Get` die `Set` -Methode und die-Methode für die Paket Variablen, um zu verhindern, dass andere Unterprogramme Sie direkt lesen und schreiben. Wenn eine Anforderung besteht, einige Variablen zwischen den Aufrufen von Teilprogrammen in derselben Sitzung verfügbar zu halten, werden diese Variablen wie globale Variablen behandelt.

Um diese Bereichs Regel zu umgehen, verwendet SSMA für Oracle gespeicherte Prozeduren wie `ssma_oracle.set_pv_varchar` für jeden Variablentyp. Für den Zugriff auf diese Variablen verwendet SSMA eine Reihe von Transaktions unabhängigen `get_*` und `set_*` -Prozeduren und-Funktionen.

| Datentyp in Oracle | SSMA `Set` -Prozedur           |
| ------------------- | ------------------------------ |
| VARCHAR             | `ssma_oracle.set_pv_varchar`   |
| DATE                | `ssma_oracle.set_pv_datetime2` |
| CHAR                | `ssma_oracle.set_pv_varchar`   |
| INT                 | `ssma_oracle.set_pv_float`     |
| GLEITKOMMAZAHL               | `ssma_oracle.set_pv_float`     |

Um zwischen Variablen aus unterschiedlichen Sitzungen zu unterscheiden, speichert SSMA die Variablen `SPID` zusammen mit Ihrem (Sitzungs Bezeichner) und der Anmeldezeit der Sitzung. Folglich behalten `get_*` die `set_*` -und-Prozeduren die Variablen unabhängig von den Sitzungen, die Sie ausführen.
