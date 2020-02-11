---
title: Zulassen der Verwendung von Zertifikaten für ausgehende Verbindungen für einen Datenbankspiegelungs-Endpunkt (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- certificates [SQL Server], database mirroring
- outbound connections [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 464c9096-10d6-4c5e-8bb1-19acba27ad9e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 43a55174bae1bb03034ea005749055701884848f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62806873"
---
# <a name="allow-a-database-mirroring-endpoint-to-use-certificates-for-outbound-connections-transact-sql"></a>Ermöglichen des Verwendens von Zertifikaten für ausgehende Verbindungen für einen Datenbankspiegelungs-Endpunkt (Transact-SQL)
  In diesem Thema werden die Schritte beschrieben, um Serverinstanzen so zu konfigurieren, dass bei der Datenbankspiegelung Zertifikate zur Authentifizierung von ausgehenden Verbindungen verwendet werden können. Die ausgehende Verbindung muss konfiguriert werden, bevor eingehende Verbindungen eingerichtet werden können.  
  
> [!NOTE]  
>  Alle Spiegelungsverbindungen auf einer Serverinstanz verwenden einen gemeinsamen Datenbankspiegelungsendpunkt. Sie müssen beim Erstellen dieses Endpunktes die Authentifizierungsmethode der Serverinstanz angeben.  
  
 Der Vorgang zum Konfigurieren der ausgehenden Verbindungen umfasst die folgenden allgemeinen Schritte:  
  
1.  Erstellen eines Datenbankhauptschlüssels in der **master** -Datenbank  
  
2.  Erstellen eines verschlüsselten Zertifikats für die Serverinstanz in der **master** -Datenbank  
  
3.  Erstellen eines Endpunktes für die Serverinstanz mithilfe ihres Zertifikats  
  
4.  Sichern des Zertifikats in einer Datei und sicheres Kopieren dieses Zertifikats zum anderen System bzw. zu den anderen Systemen  
  
 Diese Schritte müssen Sie für jeden Partner und ggf. den Zeugen ausführen.  
  
 Die folgende Prozedur beschreibt diese Schritte detailliert. Für jeden Schritt enthält die Prozedur ein Beispiel für das Konfigurieren einer Serverinstanz auf einem System namens HOST_A. Im zugehörigen Beispielabschnitt werden dieselben Schritte für eine andere Serverinstanz auf einem System namens HOST_B beschrieben.  
  
## <a name="procedure"></a>Verfahren  
  
#### <a name="to-configure-server-instances-for-outbound-mirroring-connections-on-host_a"></a>So konfigurieren Sie Serverinstanzen für ausgehende Spiegelungsverbindungen (auf HOST_A)  
  
1.  Erstellen Sie in der **master** -Datenbank den Datenbankhauptschlüssel, sofern noch keiner vorhanden ist. Zum Anzeigen der für eine Datenbank vorhandenen Schlüssel verwenden Sie die Katalogsicht [sys.symmetric_keys](/sql/relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql) .  
  
     Zum Erstellen des Datenbankhauptschlüssels verwenden Sie den folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] -Befehl:  
  
    ```  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<1_Strong_Password!>';  
    GO  
    ```  
  
     Verwenden Sie ein eindeutiges und aussagekräftiges Kennwort, und hinterlegen Sie es an einem sicheren Ort.  
  
     Weitere Informationen finden Sie unter [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) und [Erstellen eines Datenbank-Hauptschlüssels](../../relational-databases/security/encryption/create-a-database-master-key.md).  
  
2.  Erstellen Sie in der **master** -Datenbank ein verschlüsseltes Zertifikat für die Serverinstanz, das für deren ausgehende Verbindungen zur Datenbankspiegelung verwendet werden soll.  
  
     Um z. B. ein Zertifikat für das HOST_A-System zu erstellen:  
  
    > [!IMPORTANT]  
    >  Wenn Sie beabsichtigen, das Zertifikat länger als ein Jahr zu verwenden, geben Sie das Ablaufdatum in UTC-Zeit mit der EXPIRY_DATE-Option in der CREATE CERTIFICATE-Anweisung an. Es wird auch empfohlen, dass Sie SQL Server Management Studio verwenden, um eine richtlinienbasierte Verwaltungsregel zu erstellen, damit Sie benachrichtigt werden, wann die Zertifikate ablaufen. Erstellen Sie mithilfe des Dialogfelds **Neue Bedingung erstellen** der Richtlinienverwaltung diese Regel im Feld **@ExpirationDate** des Facets **Zertifikat** . Weitere Informationen finden Sie unter [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) und [Sichern von SQL Server](../../relational-databases/security/securing-sql-server.md).  
  
    ```  
    USE master;  
    CREATE CERTIFICATE HOST_A_cert   
       WITH SUBJECT = 'HOST_A certificate for database mirroring',   
       EXPIRY_DATE = '11/30/2013';  
    GO  
    ```  
  
     Weitere Informationen finden Sie unter [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).  
  
     Zum Anzeigen der Zertifikate in der **master** -Datenbank können Sie die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen verwenden:  
  
    ```  
    USE master;  
    SELECT * FROM sys.certificates;  
    ```  
  
     Weitere Informationen finden Sie unter [sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql).  
  
3.  Stellen Sie sicher, dass der Datenbank-Spiegelungsendpunkt auf jeder Serverinstanz vorhanden ist.  
  
     Wenn für die Serverinstanz bereits ein Datenbank-Spiegelungsendpunkt vorhanden ist, sollten Sie diesen Endpunkt für alle anderen Sitzungen verwenden, die Sie auf der Serverinstanz herstellen. Um festzustellen, ob auf einer Serverinstanz bereits ein Datenbank-Spiegelungsendpunkt vorhanden ist und um dessen Konfiguration anzuzeigen, verwenden Sie folgende Anweisung:  
  
    ```  
    SELECT name, role_desc, state_desc, connection_auth_desc, encryption_algorithm_desc   
       FROM sys.database_mirroring_endpoints;  
    ```  
  
     Wenn kein Endpunkt vorhanden ist, erstellen Sie einen Endpunkt, der dieses Zertifikat für ausgehende Verbindungen und für die Anmeldeinformationen des Zertifikats zur Überprüfung auf dem anderen System verwendet. Dies ist ein serverweiter Endpunkt, der von allen Spiegelungssitzungen verwendet wird, an denen die Serverinstanz beteiligt ist.  
  
     So erstellen Sie beispielsweise einen Spiegelungsendpunkt für die Beispiel-Serverinstanz auf HOST_A:  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
       STATE = STARTED  
       AS TCP (  
          LISTENER_PORT=7024  
          , LISTENER_IP = ALL  
       )   
       FOR DATABASE_MIRRORING (   
          AUTHENTICATION = CERTIFICATE HOST_A_cert  
          , ENCRYPTION = REQUIRED ALGORITHM AES  
          , ROLE = ALL  
       );  
    GO  
    ```  
  
     Weitere Informationen finden Sie unter [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).  
  
4.  Sichern Sie das Zertifikat, und kopieren Sie es zum anderen System bzw. zu den anderen Systemen. Das ist erforderlich, um eingehende Verbindungen auf dem anderen System zu konfigurieren.  
  
    ```  
    BACKUP CERTIFICATE HOST_A_cert TO FILE = 'C:\HOST_A_cert.cer';  
    GO  
    ```  
  
     Weitere Informationen finden Sie unter [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql).  
  
     Kopieren Sie dieses Zertifikat mit einer sicheren Methode Ihrer Wahl. Seien Sie äußerst vorsichtig, um Ihre Zertifikate zu schützen.  
  
 Mit dem Beispielcode in den vorherigen Schritten werden ausgehende Verbindungen auf HOST_A konfiguriert.  
  
 Jetzt müssen die entsprechenden Schritte für ausgehende Verbindungen für HOST_B ausgeführt werden. Diese Schritte werden im folgenden Beispielabschnitt veranschaulicht.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel erläutert das Konfigurieren von HOST_B für ausgehende Verbindungen.  
  
```  
USE master;  
--Create the database Master Key, if needed.  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<Strong_Password_#2>';  
GO  
-- Make a certifcate on HOST_B server instance.  
CREATE CERTIFICATE HOST_B_cert   
   WITH SUBJECT = 'HOST_B certificate for database mirroring',   
   EXPIRY_DATE = '11/30/2013';  
GO  
--Create a mirroring endpoint for the server instance on HOST_B.  
CREATE ENDPOINT Endpoint_Mirroring  
   STATE = STARTED  
   AS TCP (  
      LISTENER_PORT=7024  
      , LISTENER_IP = ALL  
   )   
   FOR DATABASE_MIRRORING (   
      AUTHENTICATION = CERTIFICATE HOST_B_cert  
      , ENCRYPTION = REQUIRED ALGORITHM AES  
      , ROLE = ALL  
   );  
GO  
--Backup HOST_B certificate.  
BACKUP CERTIFICATE HOST_B_cert TO FILE = 'C:\HOST_B_cert.cer';  
GO   
--Using any secure copy method, copy C:\HOST_B_cert.cer to HOST_A.  
```  
  
 Kopieren Sie das Zertifikat zum anderen System. Verwenden Sie dazu eine sichere Methode Ihrer Wahl. Seien Sie äußerst vorsichtig, um Ihre Zertifikate zu schützen.  
  
> [!IMPORTANT]  
>  Nach dem Einrichten von ausgehenden Verbindungen müssen Sie eingehende Verbindungen auf jeder Serverinstanz für die andere Serverinstanz bzw. die anderen Serverinstanzen konfigurieren. Weitere Informationen finden Sie unter [Ermöglichen des Verwendens von Zertifikaten für eingehende Verbindungen für einen Datenbankspiegelungs-Endpunkt &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).  
  
 Weitere Informationen zum Erstellen einer Spiegeldatenbank, einschließlich eines Transact-SQL-Beispiels, finden Sie unter [Vorbereiten einer Spiegeldatenbank auf die Spiegelung &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).  
  
 Ein Transact-SQL-Beispiel zum Einrichten einer Sitzung im Hochleistungsmodus finden Sie unter [Beispiel: Einrichten der Datenbankspiegelung mithilfe von Zertifikaten &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md).  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Sofern Sie nicht garantieren können, dass Ihr Netzwerk sicher ist, wird das Verschlüsseln bei Verbindungen zur Datenbankspiegelung empfohlen.  
  
 Verwenden Sie zum Kopieren eines Zertifikats zu einem anderen System eine sichere Kopiermethode.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Auswählen eines Verschlüsselungsalgorithmus](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [Vorbereiten einer Spiegeldatenbank auf die Spiegelung (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md)   
 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)   
 [Beispiel: Einrichten der Datenbankspiegelung mithilfe von Zertifikaten (Transact-SQL)](example-setting-up-database-mirroring-using-certificates-transact-sql.md)   
 [Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md)   
 [Problembehandlung für die Datenbankspiegelungskonfiguration (SQL Server)](troubleshoot-database-mirroring-configuration-sql-server.md)   
 [Einrichten einer verschlüsselten Spiegeldatenbank](set-up-an-encrypted-mirror-database.md)  
  
  
