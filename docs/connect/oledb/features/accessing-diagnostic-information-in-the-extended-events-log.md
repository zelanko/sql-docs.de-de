---
title: Zugreifen auf Diagnoseinformationen im Protokoll der erweiterten Ereignisse | Microsoft-Dokumentation
description: Ablaufverfolgung von OLE DB-Treiber für SQL Server und den Zugriff auf Diagnoseinformationen im Protokoll für erweiterte Ereignisse
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: dd9db627fcf79114c010cc33c2552886fb7a6dc2
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66777927"
---
# <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Zugreifen auf Diagnoseinformationen im Protokoll der erweiterten Ereignisse
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Ab [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] wurden der OLE DB Driver for SQL Server und die Datenzugriffs-Ablaufverfolgung ([Datenzugriffs-Ablaufverfolgung](https://go.microsoft.com/fwlink/?LinkId=125805)) aktualisiert, um das Abrufen von Diagnoseinformationen über Verbindungsfehler vom Verbindungsringpuffer sowie von Informationen zur Anwendungsleistung aus dem Protokoll für erweiterte Ereignisse zu erleichtern.  
  
 Informationen dazu, wie Sie das Protokoll für erweiterte Ereignisse lesen, finden Sie unter [View Event Session Data](../../../relational-databases/extended-events/advanced-viewing-of-target-data-from-extended-events-in-sql-server.md). 

  
> [!NOTE]  
>  Diese Funktion ist nur für Problembehandlung und Diagnosezwecke vorgesehen und ist möglicherweise nicht geeignet zu Überwachungs oder Sicherheitszwecken.  
  
## <a name="remarks"></a>Remarks  
 Für Verbindungsvorgänge, OLE DB-Treiber für SQL Server sendet einen Client Verbindungs-ID. Wenn die Verbindung nicht hergestellt werden kann, können Sie auf den Konnektivitätsringpuffer zugreifen ([Behandlung von Konnektivitätsproblemen in SQL Server 2008 mit dem Konnektivitätsringpuffer](https://go.microsoft.com/fwlink/?LinkId=207752)), das Feld **ClientConnectionID** suchen und Diagnoseinformationen zum Verbindungsfehler abrufen. Clientverbindungs-IDs werden nur im Ringpuffer protokolliert, wenn ein Fehler auftritt. (Wenn vor dem Senden des prelogin-Pakets keine Verbindung hergestellt werden kann, wird keine Clientverbindungs-ID generiert.) Die Clientverbindungs-ID ist eine 16-Byte-GUID. Sie können auch die Clientverbindungs-ID im erweiterten Ereignisse-Ausgabeziel suchen, wenn Ereignissen in einer Sitzung für erweiterte Ereignisse die **client_connection_id** -Aktion hinzugefügt wird. Sie können die Datenzugriffs-Ablaufverfolgung aktivieren, den Verbindungsbefehl erneut ausführen und das **ClientConnectionID** -Feld in der Datenzugriffs-Ablaufverfolgung für einen fehlgeschlagenen Vorgang beobachten, wenn Sie weitere Hilfe bei der Diagnose benötigen.  
   
  
 OLE DB-Treiber für SQL Server sendet außerdem eine threadspezifische Aktivitäts-ID. Die Aktivitäts-ID wird in den Sitzungen für erweiterte Ereignisse aufgezeichnet, wenn die Sitzungen bei aktivierter TRACK_CAUSAILITY-Option gestartet werden. Bei Leistungsproblemen mit einer aktiven Verbindung können Sie die Aktivitäts-ID aus der Datenzugriffs-Ablaufverfolgung des Clients abrufen (**ActivityID** -Feld) und dann die Aktivitäts-ID in der Ausgabe für die erweiterten Ereignisse suchen. Die Aktivitäts-ID in den erweiterten Ereignissen ist eine 16-Byte-GUID (nicht dieselbe wie die GUID für die Clientverbindungs-ID), der eine Vier-Byte-Sequenznummer angefügt wurde. Die Sequenznummer steht für die Reihenfolge einer Anforderung innerhalb eines Threads und gibt die relative Reihenfolge des Batches und der RPC-Anweisungen für den Thread an. Der **ActivityID** wird optional für SQL-Batchanweisungen und RPC-Anforderungen gesendet, wenn die Datenzugriffsablaufverfolgung aktiviert und das 18. Bit im Datenzugriffs-Ablaufverfolgungs-Konfigurationswort auf ON gestellt wird.  
  
 Im folgenden Beispiel wird [!INCLUDE[tsql](../../../includes/tsql-md.md)] zum Starten einer Sitzung für erweiterte Ereignisse verwendet, die in einem Ringpuffer gespeichert werden und die von einem Client in RPC- und Batch-Vorgängen gesendete Aktivitäts-ID aufzeichnen.  
  
```  
create event session MySession on server   
add event connectivity_ring_buffer_recorded,   
add event sql_statement_starting (action (client_connection_id)),   
add event sql_statement_completed (action (client_connection_id)),   
add event rpc_starting (action (client_connection_id)),   
add event rpc_completed (action (client_connection_id))  
add target ring_buffer with (track_causality=on)  
  
```  
  
## <a name="control-file"></a>Steuerelementdatei  
 Der Inhalt der der OLE DB-Treiber für SQL Server-Steuerelementdatei (ctrl.guid) ist:  
  
```  
{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}  0x630ff  0   MSDADIAG.ETW
{EE7FB59C-D3E8-9684-AEAC-B214EFD91B31}  0x630ff  0   MSOLEDBSQL.1  
```  
  
## <a name="mof-file"></a>MOF-Datei  
 Der Inhalt der der OLE DB-Treiber für SQL Server-Mof-Datei ist:  
  
```  
#pragma classflags("forceupdate")  
#pragma namespace ("\\\\.\\Root\\WMI")  
  
/////////////////////////////////////////////////////////////////////////////  
//  
//  MSDADIAG.ETW  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW"),  
 Guid("{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW"),  
 Guid("{8B98D3F3-3CC6-0B9C-6651-9649CCE5C752}"),  
 DisplayName("msdadiag"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace : Bid2Etw_MSDADIAG_ETW  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace_TextA : Bid2Etw_MSDADIAG_ETW_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringA"),  
     extension("RString"),  
     read  
    ]  
    object msgStr;  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace_TextW : Bid2Etw_MSDADIAG_ETW_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringW"),  
     extension("RWString"),  
     read  
    ]  
    object msgStr;  
};  
  
/////////////////////////////////////////////////////////////////////////////  
//  
//  MSOLEDBSQL.1  
  
[  
 dynamic: ToInstance,  
 Description("MSOLEDBSQL.1"),  
 Guid("{EE7FB59C-D3E8-9684-AEAC-B214EFD91B31}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSOLEDBSQL_1 : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSOLEDBSQL.1"),  
 Guid("{EE7FB59D-D3E8-9684-AEAC-B214EFD91B31}"),  
 DisplayName("MSOLEDBSQL.1"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSOLEDBSQL_1_Trace : Bid2Etw_MSOLEDBSQL_1  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSOLEDBSQL.1 formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSOLEDBSQL_1_Trace_TextA : Bid2Etw_MSOLEDBSQL_1_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringA"),  
     extension("RString"),  
     read  
    ]  
    object msgStr;  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSOLEDBSQL.1 formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSOLEDBSQL_1_Trace_TextW : Bid2Etw_MSOLEDBSQL_1_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringW"),  
     extension("RWString"),  
     read  
    ]  
    object msgStr;  
};  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Behandlung von Fehlern](../../oledb/ole-db-errors/errors.md)  
  
  
