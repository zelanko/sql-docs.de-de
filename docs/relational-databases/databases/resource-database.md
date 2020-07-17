---
title: Ressourcendatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- system objects [SQL Server]
- read-only databases
- mssqlsystemresource.mdf file
- Resource database [SQL Server]
ms.assetid: d592b2b4-bc36-4eb9-9385-8fe4dff0dced
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9ba6ba2d1238c75c29990a8ab2bd98ea419cc606
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85728376"
---
# <a name="resource-database"></a>Ressourcendatenbank
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Die Ressourcendatenbank ist eine schreibgeschützte Datenbank, die alle Systemobjekte enthält, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]enthalten sind. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Systemobjekte, z.B. sys.objects, werden physisch in der Ressourcendatenbank persistent gespeichert, logisch jedoch im sys-Schema jeder Datenbank angezeigt. Die Ressourcendatenbank enthält keine Benutzerdaten oder Benutzermetadaten.  
  
 Durch die Ressourcendatenbank wird das Upgrade auf eine neue Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu einem einfacheren und schnelleren Vorgang. In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mussten zum Aktualisieren Systemobjekte gelöscht und erstellt werden. Da die Ressourcendatenbankdatei alle Systemobjekte enthält, wird ein Upgrade nun durch Kopieren der Ressourcendatenbankdatei auf den lokalen Server durchgeführt.  
  
## <a name="physical-properties-of-resource"></a>Physische Eigenschaften der Resource-Datenbank  
 Die physischen Dateinamen der Ressourcendatenbank sind mssqlsystemresource.mdf und mssqlsystemresource.ldf. Diese Dateien befinden sich unter \<*drive*>:\Programme\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\ und dürfen nicht verschoben werden. Jede Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] besitzt eine und nur genau eine zugeordnete Datei "mssqlsystemresource.mdf"; diese Datei wird für Instanzen nicht freigegeben.  
  
> [!WARNING]  
>  Upgrades und Servicepacks bieten manchmal auch eine neue Ressourcendatenbank, die im Ordner BINN installiert wird. Ändern des Speicherorts der Ressourcendatenbank wird nicht unterstützt oder empfohlen.  
  
## <a name="backing-up-and-restoring-the-resource-database"></a>Sichern und Wiederherstellen der Resource-Datenbank  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann die Ressourcendatenbank nicht sichern. Sie können eine eigene dateigestützte oder datenträgergestützte Sicherung der Datei erstellen, indem Sie die Datei mssqlsystemresource.mdf als Binärdatei (EXE) anstatt als Datenbankdatei behandeln. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann jedoch nicht zum Wiederherstellen der Sicherungen verwendet werden. Die Wiederherstellung einer Sicherungskopie von mssqlsystemresource.mdf kann nur manuell erfolgen. Achten Sie darauf, die aktuelle Ressourcendatenbank nicht durch eine veraltete oder potenziell unsichere Version zu überschreiben.  
  
> [!IMPORTANT]  
>  Nach dem Wiederherstellen einer Sicherung von mssqlsystemresource.mdf müssen Sie alle nachfolgenden Aktualisierungen erneut anwenden.  
  
## <a name="accessing-the-resource-database"></a>Zugriff auf die Resource-Datenbank  
 Die Ressourcendatenbank sollte nur von einem Microsoft Support Services-Experten oder unter dessen Anleitung geändert werden. Die ID der Ressourcendatenbank ist immer 32767. Andere wichtige Werte, die der Ressourcendatenbank zugeordnet sind, sind die Versionsnummer und der Zeitpunkt der letzten Aktualisierung der Datenbank.  
  
 **Verwenden Sie zum Ermitteln der Versionsnummer der** Resource **-Datenbank die folgende Anweisung**:  
  
```  
SELECT SERVERPROPERTY('ResourceVersion');  
GO  
```  
  
 **Verwenden Sie zum Ermitteln, wann die** Resource **-Datenbank zuletzt aktualisiert wurde, die folgende Anweisung**:  
  
```  
SELECT SERVERPROPERTY('ResourceLastUpdateDateTime');  
GO  
```  
  
 **Wenn Sie auf die SQL-Definitionen von Systemobjekten zugreifen möchten, verwenden Sie die OBJECT_DEFINITION-Funktion:**  
  
```  
SELECT OBJECT_DEFINITION(OBJECT_ID('sys.objects'));  
GO  
```  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Systemdatenbanken](../../relational-databases/databases/system-databases.md)  
  
 [Diagnoseverbindung für Datenbankadministratoren](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)  
  
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)  
  
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)  
  
 [Starten von SQL Server im Einzelbenutzermodus](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  
