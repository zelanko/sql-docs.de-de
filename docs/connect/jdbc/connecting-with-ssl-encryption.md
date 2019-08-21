---
title: Herstellen einer Verbindung mit SSL-Verschlüsselung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ec91fa8a-ab7e-4c1e-a05a-d7951ddf33b1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5ccbd9db2ae39113ca157651bdc6dc1486307419
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028154"
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
  
 Die **trustStore**-Eigenschaft gibt den Pfad (einschließlich des Dateinamens) der trustStore-Zertifikatsdatei an. Diese enthält die Liste der Zertifikate, denen der Client vertraut. Die **trustStorePassword**-Eigenschaft gibt das Kennwort an, das verwendet wird, um die Integrität der trustStore-Daten zu überprüfen. Weitere Informationen zur Verwendung des standardmäßigen Vertrauens Speicher der JVM finden Sie unter [Konfigurieren des Clients für die SSL-Verschlüsselung](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md).  
  
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
  
 Wenn die Eigenschaft **verschlüsseln** auf **true** festgelegt ist und die **TrustServerCertificate** -Eigenschaft auf **false** festgelegt ist und der Servername in der Verbindungs Zeichenfolge nicht mit dem Servernamen im SSL-Zertifikat identisch ist, wird der folgende Fehler angezeigt: ausgestellt: `The driver couldn't establish a secure connection to SQL Server by using Secure Sockets Layer (SSL) encryption. Error: "java.security.cert.CertificateException: Failed to validate the server name in a certificate during Secure Sockets Layer (SSL) initialization."`. Ab Version 7,2 unterstützt der Treiber die Zuordnung von Platzhalter Mustern in der äußersten linken Bezeichnung des Server namens im SSL-Zertifikat.
## <a name="see-also"></a>Siehe auch  
 [Verwenden der SSL-Verschlüsselung](../../connect/jdbc/using-ssl-encryption.md)   
 [Schützen von JDBC-Treiberanwendungen](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
