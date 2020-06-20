---
title: Broker:Connection-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Connection event class
ms.assetid: d3e505f2-0a43-486f-aa92-9c8e49b2dfea
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0527fb6da8219176fccd9053b13d5f112f68d8ea
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85030630"
---
# <a name="brokerconnection-event-class"></a>Broker:Connection-Ereignisklasse
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generiert ein **Broker:Connection** -Ereignis, um den Status einer Transportverbindung zu melden, die von Service Broker verwaltet wird.  
  
## <a name="brokerconnection-event-class-data-columns"></a>Datenspalten der Broker:Connection-Ereignisklasse  
  
|Datenspalte|type|BESCHREIBUNG|Spaltennummer|Filterbar|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|`nvarchar`|Der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|**ClientProcessID**|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|Ja|  
|**DatabaseID**|`int`|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database*-Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Bestimmen Sie den Wert für eine Datenbank, indem Sie die **DB_ID** -Funktion verwenden.|3|Ja|  
|**Fehler**|`int`|Die Nachrichten-ID-Nummer in **sys. Messages** für den Text im Ereignis. Wenn dieses Ereignis einen Fehler meldet, ist dies die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlernummer.|31|Nein|  
|**EventClass**|`int`|Der Typ der aufgezeichneten Ereignisklasse. Für **Broker:Connection** lautet der Typ immer **138**.|27|Nein|  
|**EventSequence**|`int`|Die Sequenznummer für dieses Ereignis.|51|Nein|  
|**EventSubClass**|`nvarchar`|Der Verbindungsstatus dieser Verbindung. Für dieses Ereignis hat die Unterklasse einen der folgenden Werte.<br /><br /> **Verbindung**wird hergestellt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] initiiert eine Transportverbindung.<br /><br /> **Verbunden**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hat eine Transportverbindung hergestellt.<br /><br /> **Verbindung ist fehlgeschlagen**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konnte keine Transportverbindung herstellen.<br /><br /> **Schließt**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] schließt die Transportverbindung.<br /><br /> **Geschlossen**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hat die Transportverbindung geschlossen.<br /><br /> **Akzeptieren**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hat eine Transportverbindung von einer anderen Instanz akzeptiert.<br /><br /> **IO-Fehler gesendet**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist beim Senden einer Nachricht ein Transportfehler aufgetreten.<br /><br /> **IO-Fehler empfangen**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist beim Empfangen einer Nachricht ein Transportfehler aufgetreten.|21|Ja|  
|**GUID**|`uniqueidentifier`|Die Endpunkt-ID dieser Verbindung.|54|Nein|  
|**HostName**|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Verwenden Sie die **HOST_NAME** -Funktion, um den Hostnamen zu ermitteln.|8|Ja|  
|**IntegerData**|`int`|Die Angabe, wie oft diese Verbindung geschlossen wurde.|25|Ja|  
|**IsSystem**|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist.<br /><br /> 0 = Benutzer<br /><br /> 1 = System|60|Nein|  
|**LoginSid**|`image`|Die Sicherheits-ID (SID, Security Identification Number) des angemeldeten Benutzers. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|**NTDomainName**|`nvarchar`|Die Windows-Domäne, der der Benutzer angehört.|7|Ja|  
|**NTUserName**|`nvarchar`|Der Name des Benutzers, der Besitzer der Verbindung ist, die dieses Ereignis generiert hat.|6|Ja|  
|**ObjectName**|`nvarchar`|Das Konversationshandle des Dialogs.|34|Nein|  
|**ServerName**|`nvarchar`|Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|**SPID**|`int`|Die Serverprozess-ID, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem Prozess zugewiesen wurde, der diesem Client zugeordnet ist.|12|Ja|  
|**StartTime**|`datetime`|Der Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar.|14|Ja|  
|**TextData**|`ntext`|Der Text der Fehlermeldung, die sich auf dieses Ereignis bezieht. Bei Ereignissen, die keine Fehler melden, ist dieses Feld leer. Die Fehlermeldung kann eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlermeldung oder eine Windows-Fehlermeldung sein.|1|Ja|  
|**TransactionID**|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|Nein|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
