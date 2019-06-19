---
title: Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d8d6f62a-e815-425c-a80e-a63fd34ec275
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8d1aa3a5156b10050c1b5b977dae40cf0513fbfb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62927363"
---
# <a name="transact-sql-statements"></a>Transact-SQL-Anweisungen
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

In diesem Referenzthema werden die Kategorien der Anweisungen zusammengefasst, die mit Transact-SQL (T-SQL) verwendet werden. Eine Auflistung aller Anweisungen finden Sie im linken Navigationsbereich.

## <a name="backup-and-restore"></a>Sichern und Wiederherstellen
Die Backup- und Restore-Anweisungen stellen Möglichkeiten bereit, um Sicherungen zu erstellen und Wiederherstellungen aus Sicherungen vorzunehmen.  Weitere Informationen finden Sie in der [Übersicht zur Sicherung und Wiederherstellung](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).

## <a name="data-definition-language"></a>Datendefinitionssprache
Durch DDL-Anweisungen (Data Definition Language, Datendefinitionssprache) werden Datenstrukturen definiert. Verwenden Sie die Anweisungen, um Datenstrukturen in einer Datenbank zu erstellen, zu ändern oder zu löschen.
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
- UPDATE
- MERGE
- TRUNCATE TABLE

## <a name="permissions-statements"></a>Berechtigungsanweisungen
Durch Berechtigungsanweisungen wird bestimmt, welche Benutzer und Konten auf Daten zugreifen und Vorgänge ausführen können. Weitere Informationen zur Authentifizierung und zum Zugriff finden Sie im [Sicherheitscenter](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="service-broker-statements"></a>Service Broker-Anweisungen
Bei Service Broker handelt es sich um ein Feature, das native Unterstützung für Messaging- und Warteschlangenanwendungen bereitstellt. Weitere Informationen finden Sie unter [Service Broker](../../relational-databases/service-broker/event-notifications.md).

## <a name="session-settings"></a>Sitzungseinstellungen
Durch SET-Anweisungen wird bestimmt, wie die aktuelle Sitzung ausgeführte Uhrzeiteinstellungen verarbeitet. Eine Übersicht finden Sie unter [SET-Anweisungen](set-statements-transact-sql.md).
