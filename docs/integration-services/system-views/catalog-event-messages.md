---
title: catalog.event_messages | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: a31a654f-31e9-4da1-aabf-182b07848e36
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2e19ca7fac23979ecd691ed6cab45fa2cfec9564
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86912629"
---
# <a name="catalogevent_messages"></a>catalog.event_messages 

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Zeigt Informationen zu Meldungen an, die während der Vorgänge protokolliert wurden.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|Event_message_ID|BIGINT|Die eindeutige ID der Ereignismeldung.|  
|Operation_id|BIGINT|Der Typ des Vorgangs.<br /><br /> Eine Liste von Vorgangstypen finden Sie unter [catalog.operations &#40;SSISDB-Datenbank&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md).|  
|Message_time|datetimeoffset(7)|Der Zeitpunkt, zu dem die Meldung erstellt wurde.|  
|Message_type|SMALLINT|Typ der angezeigten Meldung. Weitere Informationen zu Meldungstypen finden Sie unter [catalog.operation_messages &#40;SSISDB-Datenbank&#41;](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md).|  
|Message_source_type|SMALLINT|Die Quelle der Nachricht.|  
|message|nvarchar(max)|Der Text der Meldung.|  
|Extended_info_id|BIGINT|Die ID weiterer Informationen, die sich auf die Vorgangsmeldung beziehen, finden Sie in der [catalog.extended_operation_info &#40;SSISDB Datenbank&#41;](../../integration-services/system-views/catalog-extended-operation-info-ssisdb-database.md)-Sicht.|  
|Package_name|nvarchar(260)|Der Name der Paketdatei.|  
|Event_name|nvarchar(1024)|Das der Meldung zugeordnete Laufzeitereignis.|  
|Message_source_name|nvarchar(4000)|Die Paketkomponente, die als Quelle der Nachricht dient.|  
|Message_source_id|nvarchar(38)|Die eindeutige ID der Quelle der Meldung.|  
|Subcomponent_name|nvarchar(4000)|Die Datenflusskomponente, die als Quelle der Meldung dient.<br /><br /> Wenn Meldungen von der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Engine zurückgegeben werden, wird SSIS.Pipeline in dieser Spalte angezeigt.|  
|Package_path|nvarchar(max)|Der eindeutige Pfad der Komponente innerhalb des Pakets.|  
|Execution_path|nvarchar(max)|Der vollständige Pfad vom übergeordneten Paket zu dem Punkt, an dem die Komponente ausgeführt wird.<br /><br /> Dieser Pfad zeichnet auch Iterationen einer Komponente auf.|  
|threadID|INT|ID für den Thread, der ausgeführt wird, wenn die Meldung protokolliert wird.|  
|Message_code|INT|Der der Meldung zugeordnete Code.|  
  
## <a name="remarks"></a>Bemerkungen  
 In dieser Sicht werden die folgenden Meldungsquelltypen angezeigt:  
  
|**message_source_type**|BESCHREIBUNG|  
|-------------------------------|-----------------|  
|10|Eintrag-APIs, z. B. T-SQL und gespeicherte CLR-Prozeduren|  
|20|Externer Prozess, der verwendet wurde, um das Paket (ISServerExec.exe) auszuführen|  
|30|Objekte auf Paketebene|  
|40|Ablaufsteuerungsaufgaben|  
|50|Ablaufsteuerungscontainer|  
|60|Datenflusstask|  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für den Vorgang  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin** .  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
## <a name="see-also"></a>Weitere Informationen  
 [catalog.event_message_context](../../integration-services/system-views/catalog-event-message-context.md)  
  
  
