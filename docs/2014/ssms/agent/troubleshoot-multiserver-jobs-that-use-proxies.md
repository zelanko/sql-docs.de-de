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
ms.openlocfilehash: 19de975ef5e1f22c93cec72a5014a01da5b03dd8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067464"
---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a>Problembehandlung von proxybasierten Multiserveraufträgen
  Verteilte Aufträge mit Schritten, die einem Proxy zugeordnet sind, werden unter dem Kontext des Proxykontos auf dem Zielserver ausgeführt. Wenn Auftragsschritte, die Proxykonten verwenden, beim Herunterladen vom Masterserver einen Fehler erzeugen, überprüfen Sie die **error_message** -Spalte in der **sysdownloadlist** -Tabelle der **msdb** -Datenbank auf folgende Fehlermeldungen:  
  
-   "Für den Auftragsschritt ist ein Proxykonto erforderlich, das Proxyabgleichen ist auf dem Zielserver aber deaktiviert."  
  
     Um diesen Fehler zu beheben, legen Sie den Wert für **\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server\MSSQL.** _ \<n_> **\Sqlserveragent\allowdownloader-djobstomatchproxyname** Registrierungs Unterschlüssel auf **1 (true)**. Dieser Unterschlüssel ist standardmäßig auf **0** () festgelegt `false` . Der Wert von **MSSQL.**\<*n*> ist der Instanzname. z. b. **MSSQL. 1** oder **MSSQL. 3**.  
  
-   "Proxy nicht gefunden."  
  
     Zum Beheben dieses Fehlers stellen Sie sicher, dass auf dem Zielserver ein Proxykonto vorhanden ist, das den gleichen Namen wie das Proxykonto des Masterservers hat, unter dem der Auftragsschritt ausgeführt wird.  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Multiserverumgebung](create-a-multiserver-environment.md)  
  
  
