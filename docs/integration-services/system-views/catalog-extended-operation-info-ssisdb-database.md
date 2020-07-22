---
title: catalog.extended_operation_info (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: db299b45-557d-4c62-8e14-355cdb051f63
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dfc87963af1a7d55a8368b31d1ed94ccdc04b717
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86912550"
---
# <a name="catalogextended_operation_info-ssisdb-database"></a>catalog.extended_operation_info (SSISDB-Datenbank)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Zeigt erweiterte Informationen für alle Vorgänge im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Katalog an.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|info_id|**bigint**|Der eindeutige Bezeichner (ID) der erweiterten Informationen.|  
|operation_id|**bigint**|Die eindeutige ID des Vorgangs, der den erweiterten Informationen entspricht.|  
|object_name|**nvarchar(260)**|Der Name des Objekts.|  
|object_type|**smallint**|Der Typ des von dem Vorgang betroffenen Objekts. Bei dem Objekt kann es sich um einen Ordner (`10`), ein Projekt (`20`), ein Paket (`30`), eine Umgebung (`40`) oder eine Instanz der Ausführung (`50`) handeln.|  
|reference_id|**bigint**|Die eindeutige ID des Verweises, der im Vorgang verwendet wird.|  
|status|**int**|Der Status des Vorgangs. Die möglichen Werte lauten "erstellt" (`1`), "wird ausgeführt" (`2`), "abgebrochen" (`3`), "fehlerhaft" (`4`), "ausstehend" (`5`), "unerwartet beendet" (`6`), "erfolgreich" (`7`), "wird beendet" (`8`) und "abgeschlossen" (`9`).|  
|start_time|**datetimeoffset(7)**|Datum und Uhrzeit für das Starten des Vorgangs.|  
|end_time|**datetimeoffset(7)**|Datum und Uhrzeit für das Beenden des Vorgangs.|  
  
## <a name="remarks"></a>Bemerkungen  
 Ein einzelner Vorgang kann über mehrere Zeilen mit erweiterten Informationen verfügen.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für den Vorgang  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
> [!NOTE]  
>  Wenn Sie über die Berechtigung verfügen, einen Vorgang auf dem Server auszuführen, verfügen Sie auch über die Berechtigung, Informationen zu dem Vorgang anzuzeigen. Sicherheit auf Zeilenebene wird erzwungen. Es werden nur Zeilen angezeigt, zu deren Anzeige Sie berechtigt sind.  
  
  
