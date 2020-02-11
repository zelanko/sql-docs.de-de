---
title: Zeugenserverinstanz (Assistent zum Konfigurieren der Sicherheit für die Datenbankspiegelung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.witnsrvr.f1
ms.assetid: b5763663-984a-473b-93a3-6cd3322ad41c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7db00b9deeb5faad62731aa666c54fa385be765b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62753972"
---
# <a name="witness-server-instance-configure-database-mirroring-security-wizard"></a>Zeugenserverinstanz (Assistent zum Konfigurieren der Sicherheit für die Datenbankspiegelung)
  Verwenden Sie diese Seite, um Informationen zur Serverinstanz anzugeben, die als Zeuge für die Sitzung fungieren soll.  
  
> [!NOTE]  
>  Eine Zeugenserverinstanz ist nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 **So konfigurieren Sie die Datenbankspiegelung mithilfe von SQL Server Management Studio**  
  
-   [Einrichten einer Datenbank-Spiegelungssitzung mithilfe der Windows-Authentifizierung &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Starten des Assistenten zum Konfigurieren der Sicherheit für die Datenbankspiegelung &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Tastatur  
 **Zeugen Serverinstanz**  
 Wenn bereits eine Zeugenserverinstanz angegeben ist (auf der Seite **Spiegelung** im Dialogfeld **Datenbankeigenschaften** ), wird diese Instanz angezeigt (weitere Informationen finden Sie unter [Datenbankeigenschaften &#40;Seite „Wird gespiegelt“&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)).  
  
 Andernfalls wird in diesem Listenfeld der Name des aktuellen Servers angezeigt. Beachten Sie, dass die Zeugenserverinstanz nicht die gleiche sein kann wie die Prinzipal- oder Spiegelserverinstanz.  
  
 **Herstellen einer Verbindung**  
 Wenn keine Zeugenserverinstanz festgelegt wurde, klicken Sie auf **Verbinden**. Dadurch wird das Dialogfeld **Verbindung mit Server herstellen** angezeigt, mit dem Sie die Serverinstanz festlegen und eine Verbindung herstellen können.  
  
 Klicken Sie auf **Verbinden**, wenn eine Instanz angegeben wurde, der Assistent aber keine Verbindung mit ausreichenden Berechtigungen zum Überprüfen eines vorhandenen Endpunkts herstellen konnte. Dadurch wird das Dialogfeld **Verbindung mit Server herstellen** mit einer vorausgewählten und nicht änderbaren Serverinstanz angezeigt. Geben Sie ein Domänenkonto mit ausreichender Berechtigung an, und stellen Sie eine Verbindung zur Serverinstanz her.  
  
> [!NOTE]  
>  Beim Herstellen der Verbindung mit der Serverinstanz verwendet der Assistent zum Konfigurieren der Sicherheit für die Datenbankspiegelung die Anmeldeinformationen, die im Dialogfeld **Verbindung mit Server herstellen** bereitgestellt werden. Diese unterscheiden sich von den Anmeldeinformationen einer Spiegelungssitzung, bei der die Anmeldeinformationen des Startkontos verwendet werden, unter dem die Serverinstanz als Dienst ausgeführt wird.  
  
 **Listenerport**  
 Das Verhalten dieser Option hängt auf folgende Weise davon ab, ob für diese Serverinstanz der Spiegelungsendpunkt vorhanden ist:  
  
-   Wenn für die Serverinstanz der Überwachungsport nicht vorhanden ist, wird im Textfeld **Port** die Portnummer 5022 angezeigt. Sie können jede verfügbare Portnummer eingeben, wie z. B. 7022.  
  
-   Wenn der Spiegelungsendpunkt bereits vorhanden ist, wird die Portnummer dieses Endpunkts angezeigt. Wenn Sie diesen Port ändern müssen, verwenden Sie die ALTER ENDPOINT-Anweisung. Weitere Informationen finden Sie unter [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).  
  
    > [!NOTE]  
    >  Eine Portnummer ist erforderlich.  
  
 **Endpunktname**  
 Wenn der Spiegelungsendpunkt für diese Serverinstanz vorhanden ist, wird der Endpunktname hier angezeigt. Ist der Endpunkt nicht vorhanden, dann können Sie den Namen für den Endpunkt hier festlegen.  
  
 **Durch diesen Endpunkt gesendete Daten verschlüsseln**  
 Standardmäßig ist die Verschlüsselung aktiviert. Wenn diese Option aktiviert ist, dann ist die Verschlüsselung erforderlich (nicht nur unterstützt), und es werden die Standardwerte für alle Verschlüsselungsoptionen verwendet. Weitere Informationen finden Sie unter [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).  
  
 Um die Verschlüsselung zu deaktivieren, deaktivieren Sie das Kontrollkästchen. Um die Verschlüsselung wieder zu aktivieren, aktivieren Sie das Kontrollkästchen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md)   
 [Datenbankeigenschaften &#40;Seite Wird gespiegelt&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Erstellen eines Endpunkts der Datenbankspiegelung für Windows-Authentifizierung (Transact-SQL)](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)   
 [Starten des Datenbankspiegelungs-Monitors &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Daten Bank Spiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Database Mirroring Witness](database-mirroring-witness.md)  
  
  
