---
title: Verbindung mit SQL Server zum Löschen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 030b10c2-6b88-4c2c-bf67-22994be25a60
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f82be8bf3015cedcd1e4f88724201f01f05858c3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187207"
---
# <a name="connection-to-sql-server-for-delete"></a>Verbindung zu SQL Server zum Löschen
  Wenn eine Anmeldung ohne Datenbankrolle, die über die Schreibberechtigung für die MSXDBCDC-Datenbank verfügt (z.B. die Rolle **db_owner**), versucht, eine Oracle CDC-Instanz zu löschen, wird das Dialogfeld „Verbindung mit SQL Server herstellen“ angezeigt.  
  
 In diesem Dialogfeld müssen Sie die Anmeldeinformationen für eine Anmeldung eingeben, die über die Schreibberechtigung für die MSXDBCDC-Datenbank verfügt, z.B. die Datenbankrolle **db_owner** zum Löschen der Oracle CDC-Instanz.  
  
 Geben Sie im Dialogfeld Verbindung mit SQL Server herstellen die folgenden Informationen ein.  
  
 **Servername**  
 Geben Sie den Namen des Servers ein, auf dem sich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] befindet.  
  
 **Authentifizierung**  
 Wählen Sie eine der folgenden Optionen aus:  
  
-   **Windows-Authentifizierung**  
  
-   **SQL Server-Authentifizierung**: Wenn Sie diese Option auswählen, müssen Sie den **Benutzernamen** und das **Kennwort** für den Benutzer von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeben, mit dem Sie eine Verbindung herstellen.  
  
 **enthalten**  
 Klicken Sie auf den Pfeil, um die verfügbaren Optionen anzuzeigen, die konfiguriert werden sollen. Sie können für diese Optionen auch die Standardwerte unverändert lassen. Verfügbare Optionen:  
  
-   **Verbindungstimeout**: Geben Sie den Zeitraum (in Sekunden) ein, wie lange das Programm auf die Herstellung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verbindung warten soll, bevor ein Timeoutfehler eintritt. Der Standardwert lautet **15**.  
  
-   **Ausführungstimeout**: Geben Sie den Zeitraum (in Sekunden) ein, wie lange das Programm auf die Beendigung der SQL-Befehlsausführung warten soll, bevor ein Timeoutfehler eintritt. Der Standardwert ist **30**.  
  
-   **Verbindung verschlüsseln**: Aktivieren Sie **Verbindung verschlüsseln** , um sicherzustellen, dass die hergestellte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verbindung verschlüsselt wird, um Datenschutz zu gewährleisten.  
  
-   **Erweitert:** Klicken Sie auf **Erweitert** , und geben Sie ggf. zusätzliche Verbindungseigenschaften in das Dialogfeld „Erweiterte Verbindungseigenschaften“ ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Für SQL Server-Verbindung erforderliche Berechtigungen für den CDC Service](sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
