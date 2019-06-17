---
title: Task-Editor (Seite Anmeldungen) Anmeldungen übertragen | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: ae8ebf56e4ae7c4fce3566cb7688d203b8ceb318
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66054924"
---
# <a name="transfer-logins-task-editor-logins-page"></a>Editor für den Task Anmeldungen übertragen (Seite Anmeldungen)
  Verwenden Sie die Seite **Anmeldungen** des Dialogfelds **Editor für den Task 'Anmeldungen übertragen'** , um die Eigenschaften für das Kopieren von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anmeldungen von einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in eine andere anzugeben. Weitere Informationen zu diesem Task finden Sie unter [Transfer Logins Task](control-flow/transfer-logins-task.md).  
  
> [!IMPORTANT]  
>  Wenn der Task Anmeldungen übertragen ausgeführt wird, werden auf dem Zielserver Anmeldungen mit zufällig erzeugten Kennwörtern erstellt, und die Kennwörter werden deaktiviert. Um diese Anmeldungen zu verwenden, muss ein Mitglied der festen Serverrolle **sysadmin** die Kennwörter ändern und aktivieren. Die Anmeldung **sa** kann nicht übertragen werden.  
  
## <a name="options"></a>Optionen  
 **SourceConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie auf **\<Neue Verbindung...>** , um eine neue Verbindung mit dem Quellserver herzustellen.  
  
 **DestinationConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie auf **\<Neue Verbindung...>** , um eine neue Verbindung mit dem Zielserver herzustellen.  
  
 **LoginsToTransfer**  
 Wählen Sie die vom Quell- auf den Zielserver zu kopierenden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anmeldungen aus. Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|Wert|Description|  
|-----------|-----------------|  
|**AllLogins**|Alle auf dem Quellserver vorhandenen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anmeldungen werden auf den Zielserver kopiert.|  
|**SelectedLogins**|Nur die mit **LoginsList** angegebenen Anmeldungen werden auf den Zielserver kopiert.|  
|**AllLoginsFromSelectedDatabases**|Alle Anmeldungen aus den mit **DatabasesList** angegebenen Datenbanken werden auf den Zielserver kopiert.|  
  
 **LoginsList**  
 Wählen Sie die auf dem Quellserver vorhandenen Anmeldungen aus, die auf den Zielserver kopiert werden sollen. Diese Option ist nur verfügbar, wenn für **LoginsToTransfer** **SelectedLogins**ausgewählt ist.  
  
 **DatabasesList**  
 Wählen Sie die auf dem Quellserver vorhandenen Datenbanken aus, die Anmeldungen enthalten, die auf den Zielserver kopiert werden sollen. Diese Option ist nur verfügbar, wenn für **LoginsToTransfer** **AllLoginsFromSelectedDatabases**ausgewählt ist.  
  
 **IfObjectExists**  
 Wählen Sie aus, wie der Task Anmeldungen behandeln soll, die auf dem Zielserver bereits mit demselben Namen vorhanden sind.  
  
 Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|Wert|Description|  
|-----------|-----------------|  
|**FailTask**|Der Task schlägt fehl, wenn auf dem Zielserver bereits Anmeldungen mit demselben Namen vorhanden sind.|  
|**Overwrite**|Der Task überschreibt auf dem Zielserver Anmeldungen mit demselben Namen.|  
|**Skip**|Der Task lässt Anmeldungen aus, die auf dem Zielserver mit demselben Namen vorhanden sind.|  
  
 **CopySids**  
 Wählen Sie aus, ob die den Anmeldungen zugeordneten Sicherheits-IDs auf den Zielserver kopiert werden sollen. **CopySids** muss auf **True** festgelegt sein, wenn der Task Anmeldungen übertragen zusammen mit dem Task Datenbanken übertragen verwendet wird. Anderenfalls werden die kopierten Anmeldungen von der übertragenen Datenbank nicht erkannt.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services-Tasks](control-flow/integration-services-tasks.md)   
 [Editor für den Task „Anmeldungen übertragen“ &#40;Seite „Allgemein“&#41;](general-page-of-integration-services-designers-options.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)   
 [SMO-Verbindungs-Manager](connection-manager/smo-connection-manager.md)   
 [Sichere Kennwörter](../relational-databases/security/strong-passwords.md)   
 [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
