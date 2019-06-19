---
title: Funktionseinschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
author: vainolo
ms.author: arib
manager: tomerw
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 99a0a768334ab5335591fae69e4f18060fba9866
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66506918"
---
# <a name="feature-restrictions"></a>Funktionsbezogene Einschränkungen

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

SQL Server-Angriffe erfolgen häufig über Webanwendungen, mit denen auf die Datenbank zugegriffen wird. Hierbei werden unterschiedliche Formen von Angriffen mit Einschleusung von SQL-Befehlen genutzt, um sich Informationen über die Datenbank zu verschaffen.  Im Idealfall wird Anwendungscode so entwickelt, dass keine Einschleusung von SQL-Befehlen möglich ist.  Bei einer umfangreichen Codebasis mit älterem und externem Code kann aber niemals ganz sichergestellt werden, dass alle Eventualitäten abgedeckt sind. Daher handelt es sich bei der Einschleusung von SQL-Befehlen also um eine reale Gefahr, für die ein Schutz vorhanden sein muss.  Das Ziel von Funktionseinschränkungen besteht darin, bei einigen Formen der Einschleusung von SQL-Befehlen auch dann vor der Offenlegung von Informationen über die Datenbank zu schützen, wenn die Einschleusung erfolgreich ist.

## <a name="enabling-feature-restrictions"></a>Aktivieren von Funktionseinschränkungen

Für das Aktivieren von Funktionseinschränkungen wird die gespeicherte Prozedur `sp_add_feature_restriction` wie folgt eingesetzt:

```sql
EXEC sp_add_feature_restriction <feature>, <object_class>, <object_name>
```

Die folgenden Funktionen können eingeschränkt werden:

| Funktion          | und Beschreibung |
|------------------|-------------|
| N'ErrorMessages' | Bei einer Einschränkung werden alle Benutzerdaten in der Fehlermeldung maskiert. Weitere Informationen finden Sie unter [Funktionseinschränkung für Fehlermeldungen](#error-messages-feature-restriction). |
| N'Waitfor'       | Bei einer Einschränkung erfolgt die Rückgabe des Befehls sofort ohne Verzögerung. Weitere Informationen finden Sie unter [Funktionseinschränkung WAITFOR](#waitfor-feature-restriction). |

Der Wert von `object_class` kann entweder `N'User'` oder `N'Role'` sein, um anzugeben, ob `object_name` ein Benutzername oder ein Rollenname in der Datenbank ist.

Mit dem Code im folgenden Beispiel werden alle Fehlermeldungen für den Benutzer `MyUser` maskiert:

```sql
EXEC sp_add_feature_restriction N'ErrorMessages', N'User', N'MyUser'
```

## <a name="disabling-feature-restrictions"></a>Deaktivieren von Funktionseinschränkungen

Für das Deaktivieren von Funktionseinschränkungen wird die gespeicherte Prozedur `sp_drop_feature_restriction` wie folgt eingesetzt:

```sql
EXEC sp_drop_feature_restriction <feature>, <object_class>, <object_name>
```

Im folgenden Beispiel wird die Maskierung der Fehlermeldungen für den Benutzer `MyUser` deaktiviert:

```sql
EXEC sp_drop_feature_restriction N'ErrorMessages', N'User', N'MyUser'
```

## <a name="viewing-feature-restrictions"></a>Anzeigen von Funktionseinschränkungen

Die Ansicht `sys.sql_feature_restrictions` enthält alle Funktionseinschränkungen, die derzeit für die Datenbank definiert sind. Informationen zum Modus finden Sie unter [sys.sql_feature_restrictions](../system-catalog-views/sys-sql-feature-restrictions.md).

## <a name="feature-restrictions"></a>Funktionsbezogene Einschränkungen

### <a name="error-messages-feature-restriction"></a>Funktionseinschränkung für Fehlermeldungen

Eine häufige Methode bei einem Angriff mit Einschleusung von SQL-Befehlen ist das Einschleusen von Code, der einen Fehler verursacht.  Ein Angreifer kann die Fehlermeldung untersuchen, um Informationen zum System zu erhalten und weitere Angriffe zu starten, die zielgerichteter sind.  Diese Art von Angriff kann besonders effektiv sein, wenn von einer Anwendung nicht die Ergebnisse einer Abfrage angezeigt werden, sondern die Fehlermeldungen.

Angenommen, Sie haben eine Webanwendung, die über eine Anforderung in folgender Form verfügt:

```html
http://www.contoso.com/employee.php?id=1
```

Hiermit wird die folgende Datenbankabfrage ausgeführt:

```sql
SELECT Name FROM EMPLOYEES WHERE Id=$EmpId
```

Wenn der Wert, der als Parameter `Id` an die Anforderung der Webanwendung übergeben wird, kopiert wird, um in der Datenbankabfrage „$EmpId“ zu ersetzen, kann ein Angreifer die folgende Anforderung senden:

```html
http://www.contoso.com/employee.php?id=1 AND CAST(DB_NAME() AS INT)=0
```

Der folgende Fehler wird zurückgegeben, dem der Angreifer den Namen der Datenbank entnehmen kann:

```sql
Conversion failed when converting the nvarchar value 'HR_Data' to data type int.
```

Nachdem die Funktionseinschränkung für Fehlermeldungen für den Anwendungsbenutzer in der Datenbank aktiviert wurde, wird die zurückgegebene Fehlermeldung maskiert, damit keine internen Informationen über die Datenbank offengelegt werden:

```sql
Conversion failed when converting the ****** value '******' to data type ******.
```

Der Angreifer kann auch die folgende Anforderung senden:

```html
http://www.contoso.com/employee.php?id=1 AND CAST(Salary AS TINYINT)=0
```

Daraufhin wird der folgende Fehler zurückgegeben, dem der Angreifer das Gehalt des Mitarbeiters entnehmen kann:

```sql
Arithmetic overflow error for data type tinyint, value = 140000.
```

Bei Verwendung der Funktionseinschränkung für Fehlermeldungen gibt die Datenbank Folgendes zurück:

```sql
Arithmetic overflow error for data type ******, value = ******.
```

### <a name="waitfor-feature-restriction"></a>Funktionseinschränkung WAITFOR

Bei einem Angriff mit blinder Einschleusung von SQL-Befehlen liefert eine Anwendung einem Angreifer keine Ergebnisse über den eingeschleusten SQL-Code oder per Fehlermeldung. Der Angreifer kann aber Informationen aus der Datenbank ableiten, indem er eine bedingte Abfrage erstellt, bei der die beiden Verzweigungen der Bedingung eine unterschiedliche Ausführungsdauer aufweisen. Der Angreifer kann die Antwortzeiten vergleichen und ermitteln, welche Verzweigung ausgeführt wurde, und so Informationen über das System erhalten. Die einfachste Variante dieses Angriffs ist die Verwendung der `WAITFOR`-Anweisung zum Einfügen der Verzögerung.

Angenommen, Sie haben eine Webanwendung, die über eine Anforderung in folgender Form verfügt:

```html
http://www.contoso.com/employee.php?id=1
```

Hiermit wird die folgende Datenbankabfrage ausgeführt:

```sql
SELECT Name FROM EMPLOYEES WHERE Id=$EmpId
```

Wenn der Wert, der als Parameter `Id` an die Anforderung der Webanwendung übergeben wird, kopiert wird, um in der Datenbankabfrage „$EmpId“ zu ersetzen, kann ein Angreifer die folgende Anforderung senden:

```html
http://www.contoso.com/employee.php?id=1; IF SYSTEM_USER='sa' WAITFOR DELAY '00:00:05'
```

Die Abfrage würde außerdem fünf Sekunden länger dauern, wenn das Konto `sa` verwendet wird. Wenn die Funktionseinschränkung `WAITFOR` in der Datenbank deaktiviert ist, wird die `WAITFOR`-Anweisung ignoriert, und bei diesem Angriff werden keine Informationen offengelegt.
