---
title: Prinzipalserverinstanz (Assistent zum Konfigurieren der Sicherheit für die Datenbankspiegelung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.principalsrvr.f1
ms.assetid: 58af27d7-c5dd-4669-be6b-b472bc2c8ef4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2632b5ffd5355065b4b5c1f905b3b6e5c5b6204d
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934046"
---
# <a name="principal-server-instance-configure-database-mirroring-security-wizard"></a>Prinzipalserverinstanz (Assistent zum Konfigurieren der Sicherheit für die Datenbankspiegelung)
  Auf dieser Seite können Informationen zur Serverinstanz der Prinzipaldatenbank angegeben werden. Die Prinzipaldatenbank ist die Kopie der Datenbank, durch die die Spiegelungssitzung begonnen wird. Nach Beginn der Sitzung ist die Prinzipaldatenbank die Kopie der Datenbank, von der Benutzeränderungen angenommen werden. (Im Falle eines Failovers werden die Prinzipal- und Spiegelungsrollen vertauscht, d. h. die ursprüngliche Prinzipaldatenbank bleibt möglicherweise nicht als Prinzipaldatenbank erhalten.)  
  
 **So konfigurieren Sie die Datenbankspiegelung mithilfe von SQL Server Management Studio**  
  
-   [Einrichten einer Datenbank-Spiegelungssitzung mithilfe der Windows-Authentifizierung (SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Starten des Assistenten zum Konfigurieren der Sicherheit für die Datenbankspiegelung &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Tastatur  
 **Prinzipal Serverinstanz**  
 Da eine Datenbankspiegelung in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] immer auf dem Prinzipalserver konfiguriert wird, handelt es sich bei der aktuellen Serverinstanz immer um die Prinzipalserverinstanz.  
  
 **Listenerport**  
 Das Verhalten dieser Option hängt auf folgende Weise davon ab, ob für diese Serverinstanz der Spiegelungsendpunkt vorhanden ist:  
  
-   Wenn für diese Serverinstanz der Überwachungsport nicht vorhanden ist, wird im Textfeld **Port** die Portnummer 5022 angezeigt. Sie können jede verfügbare Portnummer verwenden, wie z. B. 7022.  
  
-   Wenn der Spiegelungsendpunkt bereits vorhanden ist, wird die Portnummer dieses Endpunkts angezeigt. Wenn Sie diesen Port ändern müssen, verwenden Sie den Befehl ALTER ENDPOINT. Weitere Informationen finden Sie unter [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).  
  
> [!NOTE]  
>  Eine Portnummer ist erforderlich.  
  
 **Endpunkt Name**  
 Wenn der Spiegelungsendpunkt für diese Serverinstanz vorhanden ist, wird der Endpunktname hier angezeigt. Ist der Endpunkt nicht vorhanden, dann können Sie den Namen für den Endpunkt hier festlegen.  
  
 **Durch diesen Endpunkt gesendete Daten verschlüsseln**  
 Standardmäßig ist die Verschlüsselung aktiviert. Wenn diese Option aktiviert ist, dann ist die Verschlüsselung erforderlich (nicht nur unterstützt), und es werden die Standardwerte für alle Verschlüsselungsoptionen verwendet. Weitere Informationen finden Sie unter [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).  
  
 Um die Verschlüsselung zu deaktivieren, deaktivieren Sie das Kontrollkästchen. Um die Verschlüsselung wieder zu aktivieren, aktivieren Sie das Kontrollkästchen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md)   
 [Daten Bank Eigenschaften &#40;Seite "Spiegelung"&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Erstellen eines Datenbankspiegelungs-Endpunkts für die Windows-Authentifizierung &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)   
 [Starten Sie Datenbankspiegelungs-Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Datenbankspiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)  
  
  
