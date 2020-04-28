---
title: Erstellen eines Datenbankspiegelungs-Endpunkts für AlwaysOn-Verfügbarkeitsgruppen (SQL Server PowerShell) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], endpoint
ms.assetid: 6197bbe7-67d4-446d-ba5f-cabfa5df77f1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5fb67c488da5f01ac572ec78a369790fc9014513
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "72782988"
---
# <a name="create-a-database-mirroring-endpoint-for-alwayson-availability-groups-sql-server-powershell"></a>Erstellen eines Datenbankspiegelungs-Endpunkts für AlwaysOn-Verfügbarkeitsgruppen (SQL Server PowerShell)
  In diesem Thema wird beschrieben, wie ein Datenbankspiegelungs-Endpunkt zur Verwendung durch [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit PowerShell erstellt wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  [Sicherheit](#Security)  
  
-   **So erstellen Sie einen Datenbankspiegelungs-Endpunkt mit:**  [PowerShell](#PowerShellProcedure)  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
> [!IMPORTANT]  
>  Der RC4-Algorithmus ist veraltet. [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] Stattdessen wird die Verwendung von AES empfohlen.  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die CREATE ENDPOINT-Berechtigung oder die Mitgliedschaft in der festen Serverrolle "sysadmin". Weitere Informationen finden Sie unter [GRANT (Endpunktberechtigungen) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> PowerShell  
 **So erstellen Sie einen Datenbankspiegelungs-Endpunkt**  
  
1.  Ändern Sie das Verzeichnis (`cd`) zur Serverinstanz, für die Sie den Datenbankspiegelungs-Endpunkt erstellen möchten.  
  
2.  Verwenden Sie das `New-SqlHadrEndpoint`-Cmdlet, um den Endpunkt zu erstellen, und dann das `Set-SqlHadrEndpoint`-Cmdlet, um den Endpunkt zu starten.  
  
###  <a name="example-powershell"></a><a name="PShellExample"></a> Beispiel (PowerShell)  
 Mit den folgenden PowerShell-Befehlen wird ein Datenbankspiegelungs-Endpunkt auf einer Instanz von SQL Server (*Computer*\\*Instanz*) erstellt. Der Endpunkt verwendet Port 5022.  
  
> [!IMPORTANT]  
>  Dieses Beispiel funktioniert nur auf einer Serverinstanz, die derzeit keinen Datenbankspiegelungs-Endpunkt hat.  
  
```powershell
# Create the endpoint.  
$endpoint = New-SqlHadrEndpoint MyMirroringEndpoint -Port 5022 -Path SQLSERVER:\SQL\Machine\Instance  
  
# Start the endpoint  
Set-SqlHadrEndpoint -InputObject $endpoint -State "Started"
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So konfigurieren Sie einen Datenbankspiegelungs-Endpunkt**  
  
-   [Erstellen eines Endpunkts der Datenbankspiegelung für Windows-Authentifizierung &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Verwenden von Zertifikaten für einen Datenbankspiegelungs-Endpunkt (Transact-SQL)](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [Ermöglichen des Verwendens von Zertifikaten für ausgehende Verbindungen für einen Datenbankspiegelungs-Endpunkt &#40;Transact-SQL&#41;](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [Ermöglichen des Verwendens von Zertifikaten für eingehende Verbindungen für einen Datenbankspiegelungs-Endpunkt &#40;Transact-SQL&#41;](../../database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [Angeben einer Servernetzwerkadresse (Datenbankspiegelung)](../../database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [Angeben der Endpunkt-URL beim Hinzufügen oder Ändern eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 **So zeigen Sie Informationen zum Datenbankspiegelungs-Endpunkt an**  
  
-   [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Verfügbarkeits Gruppe &#40;Transact-SQL-&#41;](create-an-availability-group-transact-sql.md)   
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
