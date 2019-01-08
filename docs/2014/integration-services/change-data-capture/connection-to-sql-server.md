---
title: Verbindung mit SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5bb582f9-68d3-4c1e-ab02-6fc16807f1a5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 85bab82173ce0caa5997774978b616340d6e5a30
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52772962"
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
  
  
