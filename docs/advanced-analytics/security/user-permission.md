---
title: Erteilen von Datenbankberechtigungen für die skriptausführung R- und Python - SQL Server Machine Learning Services
description: Informationen zum Datenbank-Benutzerberechtigungen für die Ausführung von R und Python-Skript in SQL Server-Machine Learning-Dienste zu gewähren.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: e281f1712163aeee1846565458c2b037077c8588
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62641664"
---
# <a name="give-users-permission-to-sql-server-machine-learning-services"></a>Vergabe von Benutzerberechtigungen für SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird beschrieben, wie Sie Benutzern gestatten können über die Berechtigung zum Ausführen externer Skripts, die in SQL Server-Machine Learning-Dienste, und geben Sie Lese-, Schreib- oder Data Definition Language (DDL) Berechtigungen für Datenbanken.

Weitere Informationen finden Sie im Abschnitt "Berechtigungen" im [Sicherheit: Übersicht für das Extensibility Framework](../../advanced-analytics/concepts/security.md#permissions).

<a name="permissions-external-script"></a>

## <a name="permission-to-run-scripts"></a>Berechtigung zum Ausführen von Skripts

Wenn Sie installiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] selbst, und Sie in Ihrer eigenen Instanz R- oder Python-Skripts ausgeführt werden, die Sie Skripts in der Regel als Administrator ausführen. So können Sie implizite Berechtigung für verschiedene Vorgänge und alle Daten in der Datenbank.

Die meisten Benutzer haben jedoch nicht diese erhöhten Berechtigungen. Beispielsweise sind Benutzer in einer Organisation, die SQL-Benutzernamen verwenden, um Zugriff auf die Datenbank in der Regel nicht mit erhöhten Rechten berechtigt. Aus diesem Grund müssen für jeden Benutzer, die R- oder Python verwendet wird, Sie Benutzern von Machine Learning Services gewähren die Berechtigung zum Ausführen externer Skripts, die in jeder Datenbank, in denen die Sprache verwendet wird. So sieht wie:

```sql
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT TO [UserName]
```

> [!NOTE]
> Berechtigungen sind nicht spezifisch für die unterstützten Skriptsprache. Das heißt, sind es nicht separate Berechtigungsstufen für R-Skript im Vergleich zu Python-Skript. Wenn Sie separate Berechtigungen für diese Sprachen beibehalten möchten, installieren Sie R und Python auf separaten Instanzen.

<a name="permissions-db"></a> 

## <a name="grant-databases-permissions"></a>GRANT-Berechtigungen Datenbanken

Während ein Benutzer die Skripts ausgeführt wird, muss der Benutzer kann Daten aus anderen Datenbanken lesen. Der Benutzer müssen möglicherweise auch neue Tabellen zum Speichern der Ergebnisse und Schreiben von Daten in Tabellen erstellen.

Für jedes Windows-Benutzerkonto oder die SQL-Anmeldung, die R- oder Python-Skripts ausgeführt wird, stellen Sie sicher, dass sie die entsprechenden Berechtigungen für die betreffende Datenbank verfügt: `db_datareader` zum Lesen von Daten, `db_datawriter` zum Speichern von Objekten in der Datenbank oder `db_ddladmin` zum Erstellen von Objekten z. B. gespeicherte Prozeduren oder Tabellen mit trainiert und serialisierte Daten.

Beispielsweise die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung bietet die SQL-Anmeldung *MySQLLogin* die Rechte zum Ausführen von T-SQL-Abfragen in der *ML_Samples* Datenbank. Um diese Anweisung auszuführen, muss die SQL-Anmeldung bereits im Sicherheitskontext des Servers vorhanden sein.

```sql
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den Berechtigungen in den einzelnen Rollen finden Sie unter [Datenbankrollen](../../relational-databases/security/authentication-access/database-level-roles.md).