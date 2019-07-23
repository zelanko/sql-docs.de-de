---
title: SQL Server-Verbindung für die Instanzerstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 81d0e7e2-d8f0-4bd9-9565-218ce996f28e
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 4e38ec34f452ac286cf069bf2c88a9b8eb5578db
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086613"
---
# <a name="sql-server-connection-for-instance-creation"></a>SQL Server-Verbindung für die Instanzerstellung

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Einer der ersten Schritte beim Erstellen einer Oracle CDC-Instanz ist die Erstellung einer CDC-Datenbank auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Zielinstanz. Diese CDC-Datenbank wird für SQL Server CDC aktiviert, und für diese Aktivierung ist eine Anmeldung durch einen Benutzer erforderlich, der Mitglied der festen Serverrolle `sysadmin` ist.  
  
 Wenn ein Benutzer, der den Assistenten zum **Erstellen einer Oracle-CDC-Instanz** startet, kein Mitglied der festen Serverrolle `sysadmin` ist, wird das Dialogfeld **Verbindung mit SQL Server herstellen** geöffnet. Darin werden die Anmeldeinformationen für ein Mitglied der Rolle `sysadmin` angefordert, damit der Task zum Aktivieren der Datenbank für SQL Server CDC ausgeführt werden kann. Wenn die CDC-Datenbank erstellt wird, wird die `sysadmin` -Anmeldung verworfen, und der Vorgang wird mit der ursprünglichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung fortgesetzt, die beim Zugreifen auf die Oracle Designer Console verwendet wurde.  
  
## <a name="task-list"></a>Aufgabenliste  
 Geben Sie im Dialogfeld **Verbindung mit SQL Server herstellen** die folgenden Informationen ein.  
  
 **Servername**  
 Geben Sie den Namen des Servers ein, auf dem sich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] befindet.  
  
 **Authentifizierung**  
 Wählen Sie eine der folgenden Optionen aus:  
  
-   **Windows-Authentifizierung**  
  
-   **SQL Server-Authentifizierung**: Wenn Sie diese Option auswählen, müssen Sie den **Anmeldenamen** und das **Kennwort** für den Benutzer von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeben, mit dem Sie eine Verbindung herstellen.  
  
 Der angemeldete Benutzer muss über eine Datenbankrolle verfügen, die den Zugriff auf die MSXCDCDB-Datenbank ermöglicht. Es wird empfohlen, dass der angemeldete Benutzer außerdem Zugriff auf weitere Datenbanken hat, die verwendet werden, da der Benutzer die Daten in diesen Datenbanken sonst nicht anzeigen kann.  
  
 **Optionen**  
 Klicken Sie auf den Pfeil, um die verfügbaren Optionen anzuzeigen, die konfiguriert werden sollen. Sie können für diese Optionen auch die Standardwerte unverändert lassen. Verfügbare Optionen:  
  
-   **Verbindungstimeout**: Geben Sie den Zeitraum (in Sekunden) ein, wie lange der CDC Service for Oracle auf eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] warten soll, bevor ein Timeout eintritt. Der Standardwert lautet **15**.  
  
-   **Ausführungstimeout**: Geben Sie den Zeitraum (in Sekunden) ein, wie lange der Oracle CDC-Windows-Dienst auf die Ausführung eines Befehls wartet, bis ein Timeout eintritt. Der Standardwert ist **30**.  
  
-   **Verbindung verschlüsseln**: Wählen Sie **Verbindung verschlüsseln** für die Kommunikation zwischen dem Oracle CDC Service und der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zielinstanz aus, bei der eine verschlüsselte Verbindung verwendet werden soll.  
  
-   **Erweitert**: Klicken Sie auf **Erweitert** , und geben Sie ggf. zusätzliche Verbindungseigenschaften in das Dialogfeld „Erweiterte Verbindungseigenschaften“ ein.  
  
     Weitere Informationen zum Dialogfeld „Erweiterte Verbindungseigenschaften“ finden Sie unter [Erweiterte Verbindungseigenschaften](../../integration-services/change-data-capture/advanced-connection-properties.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen der SQL Server-Änderungsdatenbank](../../integration-services/change-data-capture/create-the-sql-server-change-database.md)   
 [SQL Server-Verbindung erfordert Berechtigungen für den CDC Designer](../../integration-services/change-data-capture/sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
