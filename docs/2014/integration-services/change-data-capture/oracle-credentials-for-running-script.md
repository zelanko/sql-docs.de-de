---
title: Oracle-Anmeldeinformationen zum Ausführen von Skripts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4a301cb0-2f5b-41ba-81bf-46b41d07f137
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 683b313e5b1065c3709c4637ddf968641612cc0b
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85438557"
---
# <a name="oracle-credentials-for-running-script"></a>Oracle Credentials for Running Script
  Um das ergänzende Oracle-Protokollierungsskript in der Oracle CDC Designer Console auszuführen, werden Sie vom Programm zum Angeben der Anmeldeinformationen des Oracle-Benutzers aufgefordert, der das Skript ausführt. Zum Ausführen dieses Skripts muss der Oracle-Benutzer über die ALTER TABLE-Berechtigung für alle zu erfassenden Tabellen und die SELECT-Berechtigung für die DBA_LOG_GROUPS-Sicht verfügen.  
  
## <a name="task-list"></a>Aufgabenliste  
 Geben Sie in diesem Dialogfeld Folgendes ein:  
  
 **Authentifizierung**  
  
 Wählen Sie eines der folgenden Szenarien aus:  
  
-   **Windows-Authentifizierung**: Wählen Sie diese Option, um die aktuellen Anmeldeinformationen für die Windows-Domäne zu verwenden. Sie können diese Option nur verwenden, wenn die Oracle-Datenbank für die Nutzung der Windows-Authentifizierung konfiguriert ist.  
  
-   **Oracle Authentication**: Wenn Sie diese Option aktivieren, müssen Sie **Benutzername** und **Kennwort** für den Benutzer der Oracle-Quelldatenbank eingeben, mit der Sie eine Verbindung herstellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [How to Manage a CDC Instance](manage-a-cdc-instance.md)   
 [Überprüfen und Generieren ergänzender Protokollierungsskripts](review-and-generate-supplemental-logging-scripts.md)  
  
  
