---
title: Erteilen von Daten Bank Berechtigungen für die Skriptausführung von R und python
description: Erteilen von Datenbankbenutzer Berechtigungen für die Ausführung von R-und python-Skripts auf SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: a6b2fb46cb2ee361d858fa460119e6960d78fda7
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345104"
---
# <a name="give-users-permission-to-sql-server-machine-learning-services"></a>Erteilen Sie Benutzern die Berechtigung zum SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird beschrieben, wie Sie Benutzern die Berechtigung zum Ausführen externer Skripts in SQL Server Machine Learning Services erteilen und Datenbanken Lese-, Schreib-oder DDL-Berechtigungen (Data Definition Language, Datendefinitionssprache) erteilen.

Weitere Informationen finden Sie im Abschnitt "Berechtigungen" unter [Sicherheitsübersicht für das Erweiterbarkeit Framework](../../advanced-analytics/concepts/security.md#permissions).

<a name="permissions-external-script"></a>

## <a name="permission-to-run-scripts"></a>Berechtigung zum Ausführen von Skripts

Wenn Sie sich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] selbst installiert haben und R-oder python-Skripts in ihrer eigenen Instanz ausführen, führen Sie in der Regel Skripts als Administrator aus. Daher verfügen Sie über die implizite Berechtigung für verschiedene Vorgänge und alle Daten in der Datenbank.

Die meisten Benutzer verfügen jedoch nicht über solche erhöhten Berechtigungen. Beispielsweise haben Benutzer in einer Organisation, die SQL-Anmeldungen für den Zugriff auf die Datenbank verwenden, in der Regel keine erhöhten Berechtigungen. Daher müssen Sie für jeden Benutzer, der R oder python verwendet, Benutzern von Machine Learning Services die Berechtigung zum Ausführen externer Skripts in jeder Datenbank erteilen, in der die Sprache verwendet wird. Gehen Sie dabei folgendermaßen vor:

```sql
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT TO [UserName]
```

> [!NOTE]
> Berechtigungen sind nicht spezifisch für die unterstützte Skriptsprache. Anders ausgedrückt: Es gibt keine separaten Berechtigungsebenen für R-Skripts im Vergleich zu python-Skripts. Wenn Sie separate Berechtigungen für diese Sprachen benötigen, installieren Sie R und python auf separaten Instanzen.

<a name="permissions-db"></a> 

## <a name="grant-databases-permissions"></a>Erteilen von Daten Bank Berechtigungen

Während ein Benutzer Skripts durchführt, muss der Benutzer möglicherweise Daten aus anderen Datenbanken lesen. Der Benutzer muss möglicherweise auch neue Tabellen zum Speichern von Ergebnissen erstellen und Daten in Tabellen schreiben.

Stellen Sie für jedes Windows-Benutzerkonto oder jede SQL-Anmeldung, die R-oder python-Skripts ausführen, sicher, dass Sie `db_datareader` über die entsprechenden Berechtigungen `db_datawriter` für die jeweilige Datenbank verfügt: zum Lesen `db_ddladmin` von Daten, zum Speichern von Objekten in der Datenbank oder zum Erstellen von Objekten. z. b. gespeicherte Prozeduren oder Tabellen mit trainierten und serialisierten Daten.

Beispielsweise gibt die folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung der SQL-Anmeldung *mysqllogin* die Rechte zum Ausführen von T-SQL-Abfragen in der *ML_Samples* -Datenbank. Um diese Anweisung auszuführen, muss die SQL-Anmeldung bereits im Sicherheitskontext des Servers vorhanden sein.

```sql
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den Berechtigungen, die in den einzelnen Rollen enthalten sind, finden Sie unter [Rollen auf Datenbankebene](../../relational-databases/security/authentication-access/database-level-roles.md).