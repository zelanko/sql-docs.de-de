---
title: Oracle-Anmeldeinformationen zum Ausführen von Skripts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 4a301cb0-2f5b-41ba-81bf-46b41d07f137
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 54aaed55b01302db08782e5d13fc2c912ead0ff2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096930"
---
# <a name="oracle-credentials-for-running-script"></a>Oracle Credentials for Running Script
  Um das ergänzende Oracle-Protokollierungsskript in der Oracle CDC Designer Console auszuführen, werden Sie vom Programm zum Angeben der Anmeldeinformationen des Oracle-Benutzers aufgefordert, der das Skript ausführt. Zum Ausführen dieses Skripts muss der Oracle-Benutzer über die ALTER TABLE-Berechtigung für alle zu erfassenden Tabellen und die SELECT-Berechtigung für die DBA_LOG_GROUPS-Sicht verfügen.  
  
## <a name="task-list"></a>Aufgabenliste  
 Geben Sie in diesem Dialogfeld Folgendes ein:  
  
 **Authentifizierung**  
  
 Wählen Sie eine der folgenden Optionen aus:  
  
-   **Windows-Authentifizierung**: Wählen Sie diese Option, um die aktuellen Anmeldeinformationen für die Windows-Domäne zu verwenden. Sie können diese Option nur verwenden, wenn die Oracle-Datenbank für die Nutzung der Windows-Authentifizierung konfiguriert ist.  
  
-   **Oracle Authentication**: Wenn Sie diese Option aktivieren, müssen Sie **Benutzername** und **Kennwort** für den Benutzer der Oracle-Quelldatenbank eingeben, mit der Sie eine Verbindung herstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Verwalten einer CDC-Instanz](manage-a-cdc-instance.md)   
 [Überprüfen und Generieren ergänzender Protokollierungsskripts](review-and-generate-supplemental-logging-scripts.md)  
  
  
