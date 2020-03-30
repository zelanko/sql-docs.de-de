---
title: Erteilen von Berechtigungen für Skripts
description: Hier erfahren Sie, wie Sie Datenbankbenutzerberechtigungen für die Ausführung von R- und Python-Skripts in SQL Server Machine Learning Services erteilen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9b8d3ea5c52c5c18f09097322fdc1e1b2321494e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "73727310"
---
# <a name="give-users-permission-to-sql-server-machine-learning-services"></a>Erteilen von Benutzerberechtigungen in SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird beschrieben, wie Sie Benutzern die Berechtigung zum Ausführen externer Skripts in SQL Server Machine Learning Services und Datenbanken Lese-, Schreib-oder DDL-Berechtigungen (Data Definition Language, Datendefinitionssprache) erteilen können.

Weitere Informationen finden Sie im Abschnitt „Berechtigungen“ unter [Sicherheitsübersicht für das Erweiterbarkeitsframework](../../advanced-analytics/concepts/security.md#permissions).

<a name="permissions-external-script"></a>

## <a name="permission-to-run-scripts"></a>Berechtigung zum Ausführen von Skripts

Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] selbst installiert haben und R- oder Python-Skripts in einer eigenen Instanz ausführen, werden diese in der Regel als Administrator ausgeführt. Deshalb haben Sie die implizite Berechtigung für viele Vorgänge und alle Daten in der Datenbank.

Die meisten Benutzer verfügen jedoch nicht über diese erhöhten Berechtigungen. Beispielsweise haben Benutzer in einer Organisation, die SQL-Konten für den Zugriff auf Datenbanken benutzen, in der Regel keine erhöhten Berechtigungen. Deshalb müssen Sie jedem Benutzer, der R oder Python verwendet, in Machine Learning Services die Berechtigung zum Ausführen externer Skripts in jeder Datenbank erteilen, in der diese Sprachen verwendet werden. Gehen Sie dabei folgendermaßen vor:

```sql
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT TO [UserName]
```

> [!NOTE]
> Berechtigungen sind nicht für die unterstützte Skriptsprache spezifisch. Es gibt also keine separaten Berechtigungsebenen für R-Skripts und Python-Skripts. Wenn Sie separate Berechtigungen für diese Sprachen anlegen müssen, sollten Sie R und Python auf separaten Instanzen installieren.

<a name="permissions-db"></a> 

## <a name="grant-databases-permissions"></a>Erteilen von Datenbankberechtigungen

Wenn ein Benutzer Skripts ausführt, benötigt dieser möglicherweise Lesezugriff auf Daten in anderen Datenbanken. Möglicherweise muss der Benutzer auch neue Tabellen erstellen, um Ergebnisse zu speichern, und Daten in Tabellen schreiben.

Stellen Sie für jedes Windows-Benutzerkonto oder SQL-Konto, über das R- oder Python-Skripts ausgeführt werden, fest, dass dieses über die entsprechenden Berechtigungen für die spezielle Datenbank verfügt: `db_datareader` für den Lesezugriff auf Daten, `db_datawriter` für das Speichern von Objekten in der Datenbank und `db_ddladmin` für das Erstellen von Objekten wie gespeicherte Prozeduren oder Tabellen, die trainierte oder serialisierte Daten enthalten.

Die folgende [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung erteilt beispielsweise dem SQL-Konto *MySQLLogin* die Rechte zum Ausführen von T-SQL-Abfragen in der Datenbank *ML_Samples*. Um diese Anweisung auszuführen, muss die SQL-Anmeldung bereits im Sicherheitskontext des Servers vorhanden sein.

```sql
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den Berechtigungen der einzelnen Rollen finden Sie unter [Rollen auf Datenbankebene](../../relational-databases/security/authentication-access/database-level-roles.md).