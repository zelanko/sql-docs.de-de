---
title: Problembehandlung von proxybasierten Multiserveraufträgen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], multiserver jobs
- jobs [SQL Server Agent], multiserver jobs using proxies
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 628475d5691969a77d2d0ba4db01441c51b8deae
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52818712"
---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a>Problembehandlung von proxybasierten Multiserveraufträgen
  Verteilte Aufträge mit Schritten, die einem Proxy zugeordnet sind, werden unter dem Kontext des Proxykontos auf dem Zielserver ausgeführt. Wenn Auftragsschritte, die Proxykonten verwenden, beim Herunterladen vom Masterserver einen Fehler erzeugen, überprüfen Sie die **error_message** -Spalte in der **sysdownloadlist** -Tabelle der **msdb** -Datenbank auf folgende Fehlermeldungen:  
  
-   "Für den Auftragsschritt ist ein Proxykonto erforderlich, das Proxyabgleichen ist auf dem Zielserver aber deaktiviert."  
  
     Sie können diesen Fehler beheben, indem Sie den Registrierungsunterschlüssel **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.***\<n*>** \SQLServerAgent\AllowDownloadedJobsToMatchProxyName** auf **1 (TRUE)** festlegen. Dieser Unterschlüssel ist standardmäßig auf festgelegt **0** (`false`). Der Wert von **MSSQL.**\<*n*> ist der Instanzname, z. B. **MSSQL. 1** oder **MSSQL.3**.  
  
-   "Proxy nicht gefunden."  
  
     Zum Beheben dieses Fehlers stellen Sie sicher, dass auf dem Zielserver ein Proxykonto vorhanden ist, das den gleichen Namen wie das Proxykonto des Masterservers hat, unter dem der Auftragsschritt ausgeführt wird.  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Multiserverumgebung](create-a-multiserver-environment.md)  
  
  
