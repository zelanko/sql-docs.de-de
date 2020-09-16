---
description: Transact-SQL-Anweisungen
title: Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/17/2020
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d8d6f62a-e815-425c-a80e-a63fd34ec275
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c89cfff4f1477503650ab8f20ceb636636fb333f
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89540568"
---
# <a name="transact-sql-statements"></a>Transact-SQL-Anweisungen

[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Eine SQL-Anweisung ist eine unteilbare Arbeitseinheit, die entweder vollständig erfolgreich ist oder vollständig erfolglos. Eine SQL-Anweisung ist ein Satz von Anweisungen, der aus Bezeichnern, Parametern, Variablen, Namen, Datentypen und reservierten SQL-Wörtern besteht, die erfolgreich kompiliert werden. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erstellt eine *implizite* Transaktion für eine SQL-Anweisung, wenn ein `BeginTransaction`-Befehl nicht den Beginn einer Transaktion angibt. Wenn die Anweisung erfolgreich ist, führt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] immer einen Commit für die implizite Transaktionen aus, und wenn der Befehl einen Fehler generiert, wird ein Rollback für die implizite Transaktion ausgeführt.  

Es gibt viele Arten von Anweisungen. Die wahrscheinlich wichtigste ist die [SELECT](../queries/select-transact-sql.md)-Anweisung, die Zeilen aus der Datenbank abruft und die Auswahl einer oder vieler Zeilen oder Spalten aus einer Tabelle oder zahlreichen Tabellen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ermöglicht. In diesem Artikel werden die Kategorien der Anweisungen zusammengefasst, die mit Transact-SQL (T-SQL) ergänzend zur `SELECT`-Anweisung verwendet werden. Eine Auflistung aller Anweisungen finden Sie im linken Navigationsbereich.

## <a name="backup-and-restore"></a>Sichern und Wiederherstellen

Die Backup- und Restore-Anweisungen stellen Möglichkeiten bereit, um Sicherungen zu erstellen und Wiederherstellungen aus Sicherungen vorzunehmen.  Weitere Informationen finden Sie in der [Übersicht zur Sicherung und Wiederherstellung](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).

## <a name="data-definition-language"></a>Datendefinitionssprache

Durch DDL-Anweisungen (Data Definition Language, Datendefinitionssprache) werden Datenstrukturen definiert. Verwenden Sie die Anweisungen, um Datenstrukturen in einer Datenbank zu erstellen, zu ändern oder zu löschen. Zu diesen Anweisungen gehören:

- ALTER
- Sortierungen
- CREATE
- DROP
- DISABLE TRIGGER
- ENABLE TRIGGER
- RENAME
- UPDATE STATISTICS

## <a name="data-manipulation-language"></a>Datenbearbeitungssprache

Die DML (Data Manipulation Language, Datenbearbeitungssprache) wirkt sich auf die in der Datenbank gespeicherten Informationen aus. Verwenden Sie diese Anweisungen, um Zeilen in der Datenbank einzufügen, zu aktualisieren und zu verändern.

- BULK INSERT
- Delete
- INSERT
- SELECT
- UPDATE
- MERGE
- TRUNCATE TABLE

## <a name="permissions-statements"></a>Berechtigungsanweisungen

Durch Berechtigungsanweisungen wird bestimmt, welche Benutzer und Konten auf Daten zugreifen und Vorgänge ausführen können. Weitere Informationen zur Authentifizierung und zum Zugriff finden Sie im [Sicherheitscenter](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="service-broker-statements"></a>Service Broker-Anweisungen

Bei Service Broker handelt es sich um ein Feature, das native Unterstützung für Messaging- und Warteschlangenanwendungen bereitstellt. Weitere Informationen finden Sie unter [Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md).

## <a name="session-settings"></a>Sitzungseinstellungen

Durch SET-Anweisungen wird bestimmt, wie die aktuelle Sitzung ausgeführte Uhrzeiteinstellungen verarbeitet. Eine Übersicht finden Sie unter [SET-Anweisungen](set-statements-transact-sql.md).
