---
title: Editor für den Task Anmeldungen übertragen (Seite Anmeldungen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferloginstask.logins.f1
helpviewer_keywords:
- Transfer Logins Task Editor
ms.assetid: bf244c24-bd45-4ece-b66b-78b488f35c5b
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 67c81901e454c4e7a47e5d448f2aa17d6a8820fa
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972810"
---
# <a name="transfer-logins-task-editor-logins-page"></a>Editor für den Task Anmeldungen übertragen (Seite Anmeldungen)
  Verwenden Sie die Seite **Anmeldungen** des Dialogfelds **Editor für den Task 'Anmeldungen übertragen'** , um die Eigenschaften für das Kopieren von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anmeldungen von einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in eine andere anzugeben. Weitere Informationen zu diesem Task finden Sie unter [Transfer Logins Task](control-flow/transfer-logins-task.md).  
  
> [!IMPORTANT]  
>  Wenn der Task Anmeldungen übertragen ausgeführt wird, werden auf dem Zielserver Anmeldungen mit zufällig erzeugten Kennwörtern erstellt, und die Kennwörter werden deaktiviert. Um diese Anmeldungen zu verwenden, muss ein Mitglied der festen Serverrolle **sysadmin** die Kennwörter ändern und aktivieren. Die Anmeldung **sa** kann nicht übertragen werden.  
  
## <a name="options"></a>Tastatur  
 **SourceConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie **\<New connection...>** auf, um eine neue Verbindung mit dem Quell Server zu erstellen.  
  
 **DestinationConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie **\<New connection...>** auf, um eine neue Verbindung mit dem Zielserver zu erstellen.  
  
 **LoginsToTransfer**  
 Wählen Sie die vom Quell- auf den Zielserver zu kopierenden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anmeldungen aus. Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|Value|Beschreibung|  
|-----------|-----------------|  
|**AllLogins**|Alle auf dem Quellserver vorhandenen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anmeldungen werden auf den Zielserver kopiert.|  
|**SelectedLogins ausgewählt**|Nur die mit **LoginsList** angegebenen Anmeldungen werden auf den Zielserver kopiert.|  
|**AllLoginsFromSelectedDatabases**|Alle Anmeldungen aus den mit **DatabasesList** angegebenen Datenbanken werden auf den Zielserver kopiert.|  
  
 **LoginsList**  
 Wählen Sie die auf dem Quellserver vorhandenen Anmeldungen aus, die auf den Zielserver kopiert werden sollen. Diese Option ist nur verfügbar, wenn für **LoginsToTransfer****SelectedLogins**ausgewählt ist.  
  
 **DatabasesList**  
 Wählen Sie die auf dem Quellserver vorhandenen Datenbanken aus, die Anmeldungen enthalten, die auf den Zielserver kopiert werden sollen. Diese Option ist nur verfügbar, wenn für **LoginsToTransfer****AllLoginsFromSelectedDatabases**ausgewählt ist.  
  
 **IfObjectExists**  
 Wählen Sie aus, wie der Task Anmeldungen behandeln soll, die auf dem Zielserver bereits mit demselben Namen vorhanden sind.  
  
 Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|Value|Beschreibung|  
|-----------|-----------------|  
|**FailTask**|Der Task schlägt fehl, wenn auf dem Zielserver bereits Anmeldungen mit demselben Namen vorhanden sind.|  
|**Overwrite**|Der Task überschreibt auf dem Zielserver Anmeldungen mit demselben Namen.|  
|**Skip**|Der Task lässt Anmeldungen aus, die auf dem Zielserver mit demselben Namen vorhanden sind.|  
  
 **CopySids**  
 Wählen Sie aus, ob die den Anmeldungen zugeordneten Sicherheits-IDs auf den Zielserver kopiert werden sollen. **CopySids** muss auf **True** festgelegt sein, wenn der Task Anmeldungen übertragen zusammen mit dem Task Datenbanken übertragen verwendet wird. Anderenfalls werden die kopierten Anmeldungen von der übertragenen Datenbank nicht erkannt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Aufgaben Integration Services](control-flow/integration-services-tasks.md)   
 [Editor für den Task Anmeldungen übertragen &#40;Seite Allgemein&#41;](general-page-of-integration-services-designers-options.md)   
 [Ausdrucks Seite](expressions/expressions-page.md)   
 [SMO-Verbindungs-Manager](connection-manager/smo-connection-manager.md)   
 [Sichere Kennwörter](../relational-databases/security/strong-passwords.md)   
 [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
