---
title: Migrieren von Datenbanken zu SQL Server unter Linux | Microsoft-Dokumentation
description: Dieser Artikel beschreibt die verschiedenen Optionen zum Migrieren von Datenbanken und die Daten in SQL Server unter Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.technology: linux
ms.assetid: 1619489d-377a-4f32-8930-d4f536539689
ms.custom: sql-linux
ms.openlocfilehash: 4571589c84d5faaed82ae251a4af262d51e30f3f
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "46712874"
---
# <a name="migrate-databases-and-structured-data-to-sql-server-on-linux"></a>Migrieren von Datenbanken und strukturierte Daten zu SQL Server unter Linux 

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Sie können Ihre Datenbanken und die Daten mit SQL Server unter Linux migrieren. Die Methode, die Sie auswählen hängt davon ab, der Quelldaten und Ihr jeweiliges Szenario. Die folgenden Abschnitte enthalten bewährte Methoden für verschiedene Szenarien mit Migration.

## <a name="migrate-from-sql-server-on-windows"></a>Migrieren von SQLServer unter Windows
Wenn Sie SQL Server-Datenbanken auf Windows, SQL Server unter Linux migrieren möchten, ist das empfohlene Verfahren, verwenden SQL Server-Sicherung und-Wiederherstellung.

1. Erstellen Sie eine Sicherung der Datenbank, auf dem Windows-Computer.
2. Übertragen Sie die Sicherungsdatei auf den SQL Server Linux-Zielcomputer.
3. Stellen Sie die Sicherung auf dem Linux-Computer. 

Ein Tutorial zum Migrieren einer Datenbank durch Sichern und Wiederherstellen finden Sie im folgende Thema:

- [Wiederherstellen eine SQL Server-Datenbank von Windows bis Linux](sql-server-linux-migrate-restore-database.md).

Es ist auch möglich, exportieren Ihre Datenbank in eine bacpac-Datei (eine komprimierte Datei, die Ihr Datenbankschema und die Daten enthält). Wenn Sie eine bacpac-Datei verfügen, können Sie diese Datei auf Ihren Linux-Computer übertragen und dann in SQL Server importieren. Weitere Informationen finden Sie in folgenden Themen:

- [Exportieren Sie und importieren Sie eine Datenbank mit SSMS oder SqlPackage.exe](sql-server-linux-migrate-ssms.md)

## <a name="migrate-from-other-database-servers"></a>Migrieren von anderen Datenbankservern
Sie können Datenbanken auf anderen Datenbanksystemen zu SQL Server unter Linux migrieren. Dies schließt Microsoft Access, DB2, MySQL, Oracle und Sybase-Datenbanken. Verwenden Sie in diesem Szenario die SQL Server Management Assistant (SSMA), um die Migration zu SQL Server unter Linux zu automatisieren. Weitere Informationen finden Sie unter [verwenden SSMA zum Migrieren von Datenbanken zu SQL Server unter Linux](sql-server-linux-migrate-ssma.md).  

## <a name="migrate-structured-data"></a>Migrieren Sie strukturierte Daten
Es gibt auch Methoden zum Importieren von Rohdaten. Sie haben möglicherweise Datendateien strukturiert, die aus anderen Datenbanken oder Datenquellen exportiert wurden. In diesem Fall können Sie die masseneinfügung für die Daten vom Bcp-Tool. Oder Sie können SQL Server Integration Services auf Windows zum Importieren der Daten in eine SQL Server-Datenbank unter Linux ausführen. SQL Server Integration Services können Sie komplexere Transformationen für die Daten während des Imports ausführen. 

Weitere Informationen zu diesen Verfahren finden Sie unter den folgenden Themen:

- [Massenkopieren von Daten mit bcp](sql-server-linux-migrate-bcp.md)
- [Extrahieren, Transformieren und Laden von Daten für SQL Server unter Linux mit SSIS](sql-server-linux-migrate-ssis.md) 
