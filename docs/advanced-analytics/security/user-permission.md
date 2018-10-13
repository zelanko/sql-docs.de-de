---
title: Vergabe von Benutzerberechtigungen für SQL Server Machine Learning Services | Microsoft-Dokumentation
description: Informationen zum Benutzer die Berechtigung zum SQL Server Machine Learning Services erteilen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/05/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: ad5c3fa3bf94bb88041c9ec81773b2a26013e517
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100331"
---
# <a name="give-users-permission-to-sql-server-machine-learning-services"></a>Vergabe von Benutzerberechtigungen für SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird beschrieben, wie Sie Benutzern gestatten können über die Berechtigung zum Ausführen externer Skripts, die in SQL Server-Machine Learning-Dienste, und geben Sie Lese-, Schreib- oder Data Definition Language (DDL) Berechtigungen für Datenbanken.

Ein SQL Server-Anmeldung oder der Windows-Benutzerkonto muss zum Ausführen von externen Skripts, die SQL Server-Daten verwenden, oder, die mit SQL Server als Compute Context ausgeführt.

Gibt das Konto Anmeldenamen oder Benutzer an die *Sicherheitsprinzipal*, die möglicherweise mehrere Ebenen des Zugriffs, je nach den Anforderungen von externen Skript:

+ Berechtigung zum Zugriff auf die Datenbank, in dem externe Skripts aktiviert sind.
+ Berechtigungen zum Lesen von Daten aus gesicherten Objekten wie Tabellen.
+ Die Fähigkeit zum Schreiben von neuer Daten in eine Tabelle, z. B. ein Modell oder Bewertungsergebnisse.
+ Die Möglichkeit zum Erstellen neuer Objekte, z. B. Tabellen, gespeicherte Prozeduren, die das externe Skript verwenden oder benutzerdefinierte Funktionen, verwenden von R oder Python-Auftrags.
+ Das Recht, neue Pakete auf dem SQL Server-Computer installieren, oder verwenden für eine Gruppe von Benutzern bereitgestellte Pakete.

Aus diesem Grund muss jede Person, die ein externes Skript mithilfe von SQL Server als Ausführungskontext führt zu einem Benutzer in der Datenbank zugeordnet werden. Sicherheit von SQL Server ist es am einfachsten, erstellen Rollen, um die Sätze von Berechtigungen, verwalten und diesen Rollen Benutzer zuweisen, statt Berechtigungen einzeln festzulegen.

Sogar Benutzer, die R- oder Python in einem externen Tool müssen eine Anmeldung oder dem Konto in der Datenbank zugeordnet werden, wenn der Benutzer muss sich um ein externes Skript in der Datenbank, oder den Zugriff auf Datenbankobjekte und Daten auszuführen. Gibt an, ob des externen Skripts, die aus einem Data Science-Remoteclient gesendet wird, oder mit einer gespeicherten T-SQL-Prozedur gestartet, sind die gleichen Berechtigungen erforderlich.

Nehmen wir beispielsweise an, dass Sie über ein externes Skript erstellt, das auf dem lokalen Computer ausgeführt wird, und Sie diesen Code in SQL Server ausführen möchten. Sie müssen sicherstellen, dass die folgenden Bedingungen erfüllt sind:

+ Die Datenbank lässt Remoteverbindungen zu.
+ Die SQL-Anmeldung oder das Windows-Konto, die Sie für den Datenbankzugriff verwendet wurde mit der SQL Server auf Instanzebene hinzugefügt.
+ Die SQL-Anmeldung oder der Windows-Benutzer benötigen die Berechtigung zum Ausführen externer Skripts. Diese Berechtigung kann in der Regel nur von einem Datenbankadministrator hinzugefügt werden.
+ Die SQL-Anmeldung oder der Windows-Benutzer muss als Benutzer mit entsprechenden Berechtigungen in jeder Datenbank hinzugefügt werden, bei denen des externen Skripts für diese Vorgänge ausführt:
  + Abrufen von Daten aus.
  + Schreiben oder Aktualisieren von Daten.
  + Erstellen von neuen Objekten, z. B. Tabellen oder gespeicherte Prozeduren.

Nach der Anmeldung oder der Windows-Benutzerkonto bereitgestellt und die erforderlichen Berechtigungen zugewiesen wurde, können Sie ein externes Skript in SQL Server ausführen, indem Sie verwenden ein Datenquellenobjekt in R oder **Revoscalepy** -Bibliothek in Python oder durch Aufrufen einer gespeicherten die Prozedur mit dem externen Skript an.

Wenn ein externes Skript von SQL Server gestartet wird, ruft die Sicherheit der Datenbank-Engine den Sicherheitskontext des Benutzers, der der Auftrag gestartet, und verwaltet die Zuordnungen des Benutzers oder der Anmeldung zu sicherungsfähigen Objekten ab.

Aus diesem Grund müssen alle externen Skripts, die von einem Remoteclient aus initiiert werden die Anmeldenamen oder Benutzer Informationen als Teil der Verbindungszeichenfolge angeben.

<a name="permissions-external-script"></a> 

## <a name="permission-to-run-scripts"></a>Berechtigung zum Ausführen von Skripts

Wenn Sie installiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] selbst, und Sie in Ihrer eigenen Instanz R- oder Python-Skripts ausgeführt werden, die Sie Skripts in der Regel als Administrator ausführen. So können Sie implizite Berechtigung für verschiedene Vorgänge und alle Daten in der Datenbank.

Die meisten Benutzer haben jedoch nicht diese erhöhten Berechtigungen. Beispielsweise sind Benutzer in einer Organisation, die SQL-Benutzernamen verwenden, um Zugriff auf die Datenbank in der Regel nicht mit erhöhten Rechten berechtigt. Aus diesem Grund müssen für jeden Benutzer, die R- oder Python verwendet wird, Sie Benutzern von Machine Learning Services gewähren die Berechtigung zum Ausführen externer Skripts, die in jeder Datenbank, in denen die Sprache verwendet wird. So sieht wie:

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!NOTE]
> Berechtigungen sind nicht spezifisch für die unterstützten Skriptsprache. Das heißt, sind es nicht separate Berechtigungsstufen für R-Skript im Vergleich zu Python-Skript. Wenn Sie separate Berechtigungen für diese Sprachen beibehalten möchten, installieren Sie R und Python auf separaten Instanzen.

<a name="permissions-db"></a> 

## <a name="grant-databases-permissions"></a>GRANT-Berechtigungen Datenbanken

Während ein Benutzer die Skripts ausgeführt wird, muss der Benutzer kann Daten aus anderen Datenbanken lesen. Der Benutzer müssen möglicherweise auch neue Tabellen zum Speichern der Ergebnisse und Schreiben von Daten in Tabellen erstellen.

Für jedes Windows-Benutzerkonto oder die SQL-Anmeldung, die R- oder Python-Skripts ausgeführt wird, stellen Sie sicher, dass sie die entsprechenden Berechtigungen für die betreffende Datenbank verfügt: `db_datareader` zum Lesen von Daten, `db_datawriter` zum Speichern von Objekten in der Datenbank oder `db_ddladmin` zum Erstellen von Objekten z. B. gespeicherte Prozeduren oder Tabellen mit trainiert und serialisierte Daten.

Beispielsweise die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung bietet die SQL-Anmeldung *MySQLLogin* die Rechte zum Ausführen von T-SQL-Abfragen in der *ML_Samples* Datenbank. Um diese Anweisung auszuführen, muss die SQL-Anmeldung bereits im Sicherheitskontext des Servers vorhanden sein.

```SQL
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den Berechtigungen in den einzelnen Rollen finden Sie unter [Datenbankrollen](../../relational-databases/security/authentication-access/database-level-roles.md).