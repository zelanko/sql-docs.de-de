---
title: Verbindung mit SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5bb582f9-68d3-4c1e-ab02-6fc16807f1a5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 09d597cb7776362c44ca53e8d544f66608d8d37c
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58377198"
---
# <a name="connection-to-sql-server"></a>Verbindung zu SQL Server
  Wenn eine Anmeldung ohne Datenbankrolle, die über die Schreibberechtigung für die MSXDBCDC-Datenbank verfügt (z.B. die Rolle **db_owner**), versucht, eine Oracle CDC-Instanz zu erstellen, wird das Dialogfeld „Verbindung mit SQL Server herstellen“ angezeigt.  
  
 In diesem Dialogfeld müssen Sie die Anmeldeinformationen für eine Anmeldung eingeben, die über die Schreibberechtigung für die MSXDBCDC-Datenbank verfügt, z.B. die Datenbankrolle **db_owner** zum Erstellen der neuen Oracle CDC-Instanz.  
  
 Geben Sie im Dialogfeld Verbindung mit SQL Server herstellen die folgenden Informationen ein.  
  
### <a name="server-name"></a>Servername  
 Geben Sie den Namen des Servers ein, auf dem sich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] befindet.  
  
### <a name="authentication"></a>Authentifizierung  
 Wählen Sie eine der folgenden Optionen aus:  
  
-   Windows-Authentifizierung  
  
-   **SQL Server-Authentifizierung**: Wenn Sie diese Option auswählen, geben Sie die **Anmeldung** und **Kennwort** für den Benutzer in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hergestellt.  
  
### <a name="options"></a>Optionen  
 Klicken Sie auf den Pfeil, um die verfügbaren Optionen anzuzeigen, die konfiguriert werden sollen. Sie können für diese Optionen auch die Standardwerte unverändert lassen. Verfügbare Optionen:  
  
-   **Verbindungstimeout**: Geben Sie den Zeitraum (in Sekunden) das Programm wartet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindung hergestellt werden, bevor ein Timeoutfehler eintritt. Der Standardwert lautet **15**.  
  
-   **Timeout für berichtsausführung**: Geben Sie den Zeitraum (in Sekunden), den das Programm wartet, bis SQL-befehlsausführung abgeschlossen ist, bevor ein Timeoutfehler eintritt. Der Standardwert ist **30**.  
  
-   **Verbindung verschlüsseln**: Wählen Sie **Verbindung verschlüsseln** um sicherzustellen, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hergestellt wird, verschlüsselte Verbindung um Datenschutz zu gewährleisten.  
  
-   **Erweitert**: Klicken Sie auf **Erweitert** , und geben Sie ggf. zusätzliche Verbindungseigenschaften in das Dialogfeld „Erweiterte Verbindungseigenschaften“ ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Für SQL Server-Verbindung erforderliche Berechtigungen für den CDC Service](sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
