---
title: Für SQL Server-Verbindung erforderliche Berechtigungen für den CDC Service | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d9e968f9-180c-4fa0-a849-98f2b1942330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 82a83d541e38bcc571fc8d46aed1edbfb01117f5
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85435347"
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-service"></a>Für SQL Server-Verbindung erforderliche Berechtigungen für den CDC Service
  Die CDC Service Configuration Console erfordert Verbindungsinformationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um die damit verbundenen Tasks auszuführen. In diesem Thema werden die Informationen beschrieben, die im Dialogfeld Verbindung mit SQL Server herstellen zum Einrichten der Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]angegeben werden können.  
  
 Das Dialogfeld Verbindung mit SQL Server herstellen wird jeweils bei Bedarf geöffnet, z. B. wenn keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verbindungsinformationen verfügbar sind oder wenn die Informationen zwar vorhanden sind, aber die Verbindung nicht die erforderlichen Berechtigungen aufweist.  
  
 In der folgenden Tabelle werden die verschiedenen Tasks beschrieben, für die eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erforderlich ist, sowie die erforderlichen Berechtigungen für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Benutzer (Anmeldung).  
  
|Aufgabe|Mindestberechtigungen|  
|----------|-------------------------|  
|Vorbereiten der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz|`dbcreator` Feste Serverrolle|  
|Erstellen einer Oracle CDC Service-SQL Server-Anmeldung zur Verwendung durch den Oracle CDC Service|`public` Feste Serverrolle|  
|Erstellen einer Oracle CDC Service-Anmeldung, die zum Registrieren des neuen Diensts in MSXDBCDC verwendet werden soll|`db_datareader` und `db_datawriter` für MSXDBCDC|  
|Bearbeiten einer Oracle CDC Service-Anmeldung, die zum Aktualisieren der Registrierung des Diensts in MSXDBCDC verwendet werden soll|`db_datareader` und `db_datawriter` für MSXDBCDC|  
|Löschen einer Oracle CDC Service-Anmeldung, die zum Aktualisieren der Registrierung des Diensts in MSXDBCDC verwendet werden soll|`db_datareader` und `db_datawriter` für MSXDBCDC|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verbindung zu SQL Server](connection-to-sql-server.md)   
 [Verbindung zu SQL Server zum Löschen](connection-to-sql-server-for-delete.md)  
  
  
