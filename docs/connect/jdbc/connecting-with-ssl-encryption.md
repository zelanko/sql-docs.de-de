---
title: Herstellen einer Verbindung mit der Verschlüsselung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: vanto
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ec91fa8a-ab7e-4c1e-a05a-d7951ddf33b1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4cb802a7173a58e02626ec7b3242a36e7ec92465
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922449"
---
# <a name="connecting-with-encryption"></a>Herstellen von Verbindungen mit einer Verschlüsselung
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Anhand der Beispiele in diesem Artikel wird veranschaulicht, wie Eigenschaften von Verbindungszeichenfolgen verwendet werden können, die es Anwendungen ermöglichen, TLS-Verschlüsselung (Transport Layer Security) in einer Java-Anwendung zu verwenden. Weitere Informationen zu den neuen Eigenschaften für Verbindungszeichenfolgen (beispielsweise **encrypt**, **trustServerCertificate**, **trustStore**, **trustStorePassword** und **hostNameInCertificate**) finden Sie unter [Setting the Connection Properties (Festlegen der Verbindungseigenschaften)](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Wenn die Eigenschaften **encrypt** und **trustServerCertificate** auf **TRUE** festgelegt sind, wird von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] keine Überprüfung des TLS-Zertifikats für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt. Dies ist normalerweise zum Zulassen von Verbindungen in Testumgebungen erforderlich, beispielsweise wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz nur über ein selbst signiertes Zertifikat verfügt.  
  
 Im folgenden Codebeispiel wird das Festlegen der **trustServerCertificate**-Eigenschaft in einer Verbindungszeichenfolge veranschaulicht:  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true;trustServerCertificate=true";  
```  
  
 Wenn die **encrypt**-Eigenschaft auf **TRUE** und die **trustServerCertificate**-Eigenschaft auf **FALSE** festgelegt ist, wird von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] eine Überprüfung des TLS-Zertifikats für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt. Das Überprüfen des Serverzertifikats ist Teil des TLS-Handshakes und stellt sicher, dass es sich bei dem Server tatsächlich um den Server handelt, mit dem eine Verbindung hergestellt werden soll. Zum Überprüfen des Serverzertifikats müssen die Vertrauensinformationen zur Verbindungszeit explizit mithilfe der **trustStore**-Verbindungseigenschaft und der **trustStorePassword**-Verbindungseigenschaft oder implizit mithilfe des Standardvertrauensspeichers der zugrunde liegenden Java Virtual Machine (JVM) übermittelt werden.  
  
 Die **trustStore**-Eigenschaft gibt den Pfad (einschließlich des Dateinamens) der trustStore-Zertifikatsdatei an. Diese enthält die Liste der Zertifikate, denen der Client vertraut. Die **trustStorePassword**-Eigenschaft gibt das Kennwort an, das verwendet wird, um die Integrität der trustStore-Daten zu überprüfen. Weitere Informationen zur Verwendung des Standardvertrauensspeichers von JVM finden Sie unter [Konfigurieren des Clients für die Verschlüsselung](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md).  
  
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
  
 Wenn die **encrypt**-Eigenschaft auf **TRUE** und die **trustServerCertificate**-Eigenschaft auf **FALSE** festgelegt ist, und der Servername in der Verbindungszeichenfolge nicht dem Servernamen im TLS-Zertifikat entspricht, wird der folgende Fehler ausgegeben: `The driver couldn't establish a secure connection to SQL Server by using Secure Sockets Layer (SSL) encryption. Error: "java.security.cert.CertificateException: Failed to validate the server name in a certificate during Secure Sockets Layer (SSL) initialization."`. Ab Version 7.2 unterstützt der Treiber die Zuordnung von Platzhaltermustern in der ganz links stehenden Bezeichnung des Servernamens im TLS-Zertifikat.

## <a name="see-also"></a>Weitere Informationen

 [Verwenden von Verschlüsselung](../../connect/jdbc/using-ssl-encryption.md) [Schützen von JDBC-Treiberanwendungen](../../connect/jdbc/securing-jdbc-driver-applications.md)