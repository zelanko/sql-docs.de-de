---
title: PowerShell-Cmdlet für die Migrationsauswertung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 117250d3-9982-47fe-94fd-6f29f6159940
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 769948242c747abdfb1fd6e32606df6a5800a9bb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68054442"
---
# <a name="powershell-cmdlet-for-migration-evaluation"></a>PowerShell-Cmdlet für die Migrationsauswertung
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Das Cmdlet Save-SqlMigrationReport ist ein Tool zur Auswertung der Eignung mehrerer Objekte einer SQL Server-Datenbank für die Migration. Derzeit beschränkt es sich noch auf die Auswertung der Migrationseignung von In-Memory-OLTP. Das Cmdlet kann in einer erweiterten Windows PowerShell-Umgebung und in Sqlps ausgeführt werden.  
  
## <a name="syntax"></a>Syntax  
  
```powershell  
Save-SqlMigrationReport [ -MigrationType OLTP ] [ -Server server -Database database [ -Object object_name ] ]  |  [ -InputObject smo_object ] -FolderPath path  
```  
  
#### <a name="parameters"></a>Parameter  
 Die Parameter werden in der folgenden Tabelle erläutert.  
  
|Parameter|und Beschreibung|  
|----------------|-----------------|  
|MigrationType|Der Typ des Migrationsszenarios, den das Cmdlet überprüft. Derzeit ist der einzige Wert die Standard-OLTP. Optional.|  
|Server|Der Name der SQL Server-Zielinstanz. In der Windows PowerShell-Umgebung obligatorisch, wenn der Parameter -InputObject fehlt. Optional in SQLPS.|  
|Datenbank|Der Name der SQL Server-Zieldatenbank. In der Windows PowerShell-Umgebung obligatorisch, wenn der Parameter -InputObject fehlt. Optional in SQLPS.|  
|Objekt|Der Name des Zieldatenbankobjekts. Kann eine Tabelle oder eine gespeicherte Prozedur sein.|  
|InputObject|Das SMO-Zielobjekt des Cmdlets. In der Windows PowerShell-Umgebung obligatorisch, wenn die Parameter -Server und -Database fehlen. Optional in SQLPS.|  
|FolderPath|Der Ordner, in dem das Cmdlet die generierten Berichte ablegen soll. Erforderlich.|  
  
## <a name="results"></a>Ergebnisse  
 Unter dem im -FolderPath-Parameter angegebenen Ordner werden zwei Ordner erstellt: „Tables“ (Tabellen) und „Stored Procedures“ (gespeicherte Prozeduren). Wenn das Zielobjekt eine Tabelle ist, wird der Bericht zu diesem Objekt im Ordner "Tables" abgelegt. Andernfalls wird es im Ordner "Stored Procedures" abgelegt.  
  
  
