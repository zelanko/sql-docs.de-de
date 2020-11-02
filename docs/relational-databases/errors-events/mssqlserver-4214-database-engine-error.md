---
description: MSSQLSERVER_
title: MSSQLSERVER_4214
ms.custom: ''
ms.date: 08/20/2020
ms.prod: sql
ms.reviewer: ramakoni1, pijocoder, suresh-kandoth, Masha
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 4214 (Database Engine error)
ms.assetid: ''
author: suresh-kandoth
ms.author: ramakoni
ms.openlocfilehash: 0a04ec00e94dca9a4d940a3b0182123f0716d472
ms.sourcegitcommit: ead0b8c334d487a07e41256ce5d6acafa2d23c9d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92418845"
---
# <a name="mssqlserver_4214"></a>MSSQLSERVER_4214
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

## <a name="details"></a>Details

|attribute|Wert|
|---|---|
|Produktname|SQL Server|
|Ereignis-ID|4214|
|Ereignisquelle|MSSQLSERVER|
|Komponente|SQLEngine|
|Symbolischer Name|DMPX_NODBBACKUP|
|Meldungstext|BACKUP LOG cannot be performed because there is no current database backup (BACKUP LOG kann nicht ausgeführt werden, weil keine aktuelle Datenbanksicherung vorhanden ist)|
||

## <a name="explanation"></a>Erklärung

Der Fehler wird ausgelöst, wenn Sie versuchen, eine Transaktionsprotokollsicherung durchzuführen, bevor Sie eine vollständige Sicherung einer Datenbank durchführen. Bevor Sie versuchen, das Transaktionsprotokoll für eine Datenbank zu sichern, müssen Sie eine vollständige Datenbanksicherung durchführen. Außerdem wird Ihnen im Fehlerprotokoll die folgende Meldung angezeigt:

> \<Datetime> Sicherungsfehler: 3041, Schweregrad: 16, Status: 1.  
\<Datetime>  Backup     BACKUP failed to complete the command BACKUP LOG \<db_name>. (BACKUP-Fehler beim Abschließen des Befehls BACKUP LOG \<db_name>.) Ausführliche Informationen finden Sie im Sicherungsanwendungsprotokoll.

## <a name="user-action"></a>Benutzeraktion

Führen Sie eine vollständige Datenbanksicherung durch, bevor Sie versuchen, das Transaktionsprotokoll für eine Datenbank zu sichern.

## <a name="more-information"></a>Weitere Informationen

Weitere Informationen finden Sie unter: [Sichern und Wiederherstellen von SQL Server-Datenbanken.](/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases)