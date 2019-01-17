---
title: Festlegen oder Ändern der Serversortierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/03/2017
ms.prod: sql
ms.reviewer: carlrab
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- server collations [SQL Server]
- collations [SQL Server], server
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 231cc69c164e9ac4d91477710f959b073420c08e
ms.sourcegitcommit: 4df7db58095384152195039d91a01d2bee6bd07d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/06/2018
ms.locfileid: "52954394"
---
# <a name="set-or-change-the-server-collation"></a>Festlegen oder Ändern der Serversortierung

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Die Serversortierung fungiert als Standardsortierung für alle Systemdatenbanken, die zusammen mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installiert werden, sowie für alle neu erstellten Benutzerdatenbanken. Sie sollten die Sortierung auf Serverebene sorgfältig auswählen, da sie sich auf Folgendes auswirkt:
 - Sortier- und Vergleichsregeln in `=`, `JOIN`, `ORDER BY` und anderen Operatoren, die Textdaten vergleichen.
 - Sortierung der Spalten `CHAR`, `VARCHAR`, `NCHAR` und `NVARCHAR` in Systemansichten, Systemfunktionen und den Objekten in TempDB (z. B. temporäre Tabellen).
 - Namen von Variablen, Cursors und `GOTO`-Bezeichnungen. Die Variablen @pi und @PI werden als verschiedene Variablen betrachtet, wenn die Sortierung auf Serverebene die Groß-/Kleinschreibung beachtet, und wenn nicht, werden sie als identische Variablen betrachtet.
  
## <a name="setting-the-server-collation-in-sql-server"></a>Festlegen der Serversortierung in SQL Server

  Die Serversortierung wird bei der Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angegeben. Die Standardsortierung auf Serverebene ist **SQL_Latin1_General_CP1_CI_AS**. Nur-Unicode-Sortierungen können nicht als Sortierung auf Serverebene festgelegt werden. Weitere Informationen finden Sie unter [Serverkonfiguration – Sortierung](/sql/sql-server/install/server-configuration-collation.md).
  
## <a name="changing-the-server-collation-in-sql-server"></a>Ändern der Serversortierung in SQL Server

 Das Ändern der Standardsortierung für eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann ein komplexer Vorgang sein, der die folgenden Schritte umfasst:  
  
- Sicherstellen, dass Ihnen alle Informationen oder Skripts zur Verfügung stehen, die zum erneuten Erstellen der Benutzerdatenbanken und aller darin enthaltenen Objekte erforderlich sind.  
  
- Exportieren aller Daten mithilfe eines Tools wie z. B. dem [bcp Utility](../../tools/bcp-utility.md). Weitere Informationen finden Sie unter [Massenimport und -export von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
- Löschen aller Benutzerdatenbanken.  
  
- Neuerstellen der Masterdatenbank unter Angabe der neuen Sortierung in der SQLCOLLATION-Eigenschaft des **setup** -Befehls. Zum Beispiel:  
  
    ```sql  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]
    /SQLCOLLATION=CollationName  
    ```  
  
     Weitere Informationen finden Sie unter [Neuerstellen von Systemdatenbanken](../../relational-databases/databases/rebuild-system-databases.md).  
  
- Erstellen aller Datenbanken und aller darin enthaltenen Objekte.  
  
- Importieren aller Daten.  
  
> [!NOTE]  
> Anstatt die Standardsortierung einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu ändern, können Sie eine Standardsortierung für alle neu zu erstellenden Datenbanken angeben.  
  
## <a name="setting-the-server-collation-in-managed-instance"></a>Festlegen der Serversortierung in der verwalteten Instanz

Die Serversortierung in der verwalteten Azure SQL-Datenbank-Instanz (Vorschauversion) kann beim Erstellen der Instanz festgelegt werden (derzeit nur mit PowerShell). Die Standardsortierung auf Serverebene ist **SQL_Latin1_General_CP1_CI_AS**. Nur-Unicode- und die neuen UTF-8-Sortierungen können nicht als Serversortierungen festgelegt werden.
Eine Skriptvorlage zur Veranschaulichung des Festlegens der Sortierung auf Serverebene in der verwalteten Azure SQL-Datenbank-Instanz finden Sie unter [Festlegen der Sortierung für die verwaltete Instanz mithilfe einer Resource Manager-Vorlage](https://docs.microsoft.com/azure/sql-database/scripts/sql-managed-instance-create-powershell-azure-resource-manager-template). Wenn Sie Datenbanken von SQL Server zur verwalteten Instanz migrieren, überprüfen Sie die Serversortierung in der SQL Server-Quelle mit der `SERVERPROPERTY(N'Collation')`-Funktion, und erstellen Sie eine verwaltete Instanz, die der Sortierung der SQL Server-Instanz entspricht. Die Migration einer Datenbank aus SQL Server in eine verwaltete Instanz mit Sortierungen auf Serverebene, die nicht übereinstimmen, kann zu einigen unerwarteten Abfragefehlern führen. Die Sortierung auf Serverebene kann bei vorhandenen verwalteten Instanzen nicht geändert werden.

## <a name="see-also"></a>Weitere Informationen

 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)   
 [Festlegen oder Ändern der Datenbanksortierung](../../relational-databases/collations/set-or-change-the-database-collation.md)   
 [Festlegen oder Ändern der Spaltensortierung](../../relational-databases/collations/set-or-change-the-column-collation.md)   
 [Neuerstellen von Systemdatenbanken](../../relational-databases/databases/rebuild-system-databases.md)  
 
