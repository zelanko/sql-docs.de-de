---
title: Herstellen einer Verbindung mit SSL-Verschlüsselung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ec91fa8a-ab7e-4c1e-a05a-d7951ddf33b1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14f33ac9e6ab8d17954039f4ae0fca1f11e46af5
ms.sourcegitcommit: 879a5c6eca99e0e9cc946c653d4ced165905d9c6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "55737131"
---
# <a name="connecting-with-ssl-encryption"></a>Herstellen von Verbindungen mit SSL-Verschlüsselung
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  In diesem Beispiel wird veranschaulicht, wie Eigenschaften von Verbindungszeichenfolgen verwendet werden, mit denen Anwendungen die SSL-Verschlüsselung (Secure Sockets Layer) in einer Java-Anwendung verwenden können. Weitere Informationen zu den neuen Eigenschaften für Verbindungszeichenfolgen (beispielsweise **encrypt**, **trustServerCertificate**, **trustStore**, **trustStorePassword** und **hostNameInCertificate**) finden Sie unter [Setting the Connection Properties (Festlegen der Verbindungseigenschaften)](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Wenn die **encrypt**-Eigenschaft auf **TRUE** und die **trustServerCertificate**-Eigenschaft auf **TRUE** festgelegt ist, wird von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] keine Überprüfung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-SSL-Zertifikats ausgeführt. Dies ist normalerweise zum Zulassen von Verbindungen in Testumgebungen erforderlich, beispielsweise wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz nur über ein selbst signiertes Zertifikat verfügt.  
  
 Im folgenden Codebeispiel wird das Festlegen der **trustServerCertificate**-Eigenschaft in einer Verbindungszeichenfolge veranschaulicht:  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true;trustServerCertificate=true";  
```  
  
 Wenn die **encrypt**-Eigenschaft auf **TRUE** und die **trustServerCertificate**-Eigenschaft auf **FALSE** festgelegt ist, wird die Überprüfung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-SSL-Zertifikats von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ausgeführt. Das Überprüfen des Serverzertifikats ist Teil des SSL-Handshakes und stellt sicher, dass es sich bei dem Server tatsächlich um den Server handelt, mit dem eine Verbindung hergestellt werden soll. Zum Überprüfen des Serverzertifikats müssen die Vertrauensinformationen zur Verbindungszeit explizit mithilfe der **trustStore**-Verbindungseigenschaft und der **trustStorePassword**-Verbindungseigenschaft oder implizit mithilfe des Standardvertrauensspeichers der zugrunde liegenden Java Virtual Machine (JVM) übermittelt werden.  
  
 Die **trustStore**-Eigenschaft gibt den Pfad (einschließlich des Dateinamens) der trustStore-Zertifikatsdatei an. Diese enthält die Liste der Zertifikate, denen der Client vertraut. Die **trustStorePassword**-Eigenschaft gibt das Kennwort an, das verwendet wird, um die Integrität der trustStore-Daten zu überprüfen. Weitere Informationen zur Verwendung des standardvertrauensspeichers der JVM finden Sie unter den [Konfigurieren des Clients für SSL-Verschlüsselung](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md).  
  
 Im folgenden Codebeispiel wird das Festlegen der **trustStore**-Eigenschaft und der **trustStorePassword**-Eigenschaft in einer Verbindungszeichenfolge veranschaulicht:  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword";  
```  
  
 Der JDBC-Treiber stellt die zusätzliche Eigenschaft **hostNameInCertificate** bereit, mit der der Hostname des Servers angegeben wird. Der Wert dieser Eigenschaft muss mit der subject-Eigenschaft des Zertifikats übereinstimmen.  
  
 Im folgenden Codebeispiel wird das Verwenden der **hostNameInCertificate**-Eigenschaft in einer Verbindungszeichenfolge veranschaulicht:  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword" +  
     "hostNameInCertificate=hostName";  
```  
  
> [!NOTE]  
>  Sie können den Wert von Verbindungseigenschaften auch mithilfe der entsprechenden **Setter**-Methoden festlegen, die von der [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)-Klasse bereitgestellt werden.  
  
 Wenn die **verschlüsseln** -Eigenschaftensatz auf **"true"** und **TrustServerCertificate** -Eigenschaftensatz auf **"false"** und wenn der Servername in der Verbindungszeichenfolge entspricht nicht den Servernamen im SSL-Zertifikat, der folgende Fehler ausgegeben: `The driver couldn't establish a secure connection to SQL Server by using Secure Sockets Layer (SSL) encryption. Error: "java.security.cert.CertificateException: Failed to validate the server name in a certificate during Secure Sockets Layer (SSL) initialization."`. Ab Version 7.2 unterstützt der Treiber die Platzhalter-Mustervergleich in der äußersten linken Bezeichnung des Servernamens im SSL-Zertifikat.
## <a name="see-also"></a>Weitere Informationen  
 [Using SSL Encryption (Verwenden der SSL-Verschlüsselung)](../../connect/jdbc/using-ssl-encryption.md)   
 [Sichern von JDBC-Treiberanwendungen](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
