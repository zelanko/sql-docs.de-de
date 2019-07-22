---
title: Wrapper und Schnittstellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 27fc9b72-9f21-4728-abcb-5c015f28a6ab
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7be51a27364107afe6b79ebcce5de109909b1836
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916064"
---
# <a name="wrappers-and-interfaces"></a>Wrapper und Schnittstellen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] unterstützt Schnittstellen, mit denen Sie einen Proxy einer Klasse erstellen können, sowie Wrapper, die Ihnen über eine Proxyschnittstelle den Zugriff auf Erweiterungen der für [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] spezifischen JDBC-API ermöglichen.

## <a name="wrappers"></a>Wrapper

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] unterstützt die java.sql.Wrapper-Schnittstelle. Diese Schnittstelle bietet einen Mechanismus für den Zugriff auf Erweiterungen der für [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] spezifischen JDBC-API über eine Proxyschnittstelle.

Die Java. SQL. Wrapper-Schnittstelle definiert zwei Methoden: **isWrapperFor** und **Unwrap**. Mit der Methode **isWrapperFor** wird überprüft, ob das angegebene Eingabeobjekt diese Schnittstelle implementiert. Die Methode**unwrap** gibt ein Objekt zurück, das diese Schnittstelle implementiert, um den Zugriff auf die für [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] spezifischen Methoden zu ermöglichen.

die **isWrapperFor** -Methode und die **Unwrap** -Methode werden wie folgt verfügbar gemacht:

- [isWrapperFor-Methode &#40;SQLServerCallableStatement&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlservercallablestatement.md)

- [unwrap-Methode &#40;SQLServerCallableStatement&#41;](../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)

- [isWrapperFor-Methode &#40;SQLServerConnectionPoolDataSource&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverconnectionpooldatasource.md)

- [unwrap-Methode &#40;SQLServerConnectionPoolDataSource&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverconnectionpooldatasource.md)

- [isWrapperFor-Methode &#40;SQLServerDataSource&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)

- [Unwrap- &#40;Methode SQLServerDataSource&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)

- [isWrapperFor-Methode &#40;SQLServerPreparedStatement&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md)

- [unwrap-Methode &#40;SQLServerPreparedStatement&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)

- [isWrapperFor-Methode &#40;SQLServerStatement&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)

- [Unwrap- &#40;Methode (SQLServerStatement)&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)

- [isWrapperFor-Methode &#40;SQLServerXADataSource&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverxadatasource.md)

- [Unwrap- &#40;Methode SQLServerXADataSource&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md)

## <a name="interfaces"></a>Schnittstellen

Ab [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] JDBC-Treiber 3.0 stehen einem Anwendungsserver Schnittstellen für den Zugriff auf eine treiberspezifische Methode über die zugehörige Klasse zur Verfügung. Der Anwendungsserver kann die Klasse durch Erstellen eines Proxy umschließen, wodurch die [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-spezifischen Funktionen über eine Schnittstelle verfügbar gemacht werden. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] unterstützt Schnittstellen, die über die [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-spezifischen Methoden und Konstanten verfügen, sodass ein Anwendungsserver einen Proxy der Klasse erstellen kann.

Die Schnittstellen sind von Java-Standardschnittstellen abgeleitet, damit Sie nach dem Entpacken dasselbe Objekt für den Zugriff auf die treiberspezifischen Funktionen oder die generischen [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-Funktionen verwenden können.

Die folgenden Schnittstellen wurden hinzugefügt:

- [ISQLServerCallableStatement](../../connect/jdbc/reference/isqlservercallablestatement-interface.md)

- [ISQLServerConnection](../../connect/jdbc/reference/isqlserverconnection-interface.md)

- [ISQLServerDataSource](../../connect/jdbc/reference/isqlserverdatasource-interface.md)

- [ISQLServerPreparedStatement](../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)

- [ISQLServerResultSet](../../connect/jdbc/reference/isqlserverresultset-interface.md)

- [ISQLServerStatement](../../connect/jdbc/reference/isqlserverstatement-interface.md)

## <a name="example"></a>Beispiel

### <a name="description"></a>und Beschreibung

In diesem Beispiel wird veranschaulicht, wie der Zugriff auf eine [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-spezifische Funktion über ein DataSource-Objekt erfolgt. Die Klasse „DataSource“ wurde möglicherweise von einem Anwendungsserver umschlossen. Für den Zugriff auf die JDBC-Treiber-spezifische Funktion oder Konstante können Sie die Datenquelle in eine ISQLServerDataSource-Schnittstelle entpacken und die darin deklarierten Funktionen verwenden.

### <a name="code"></a>Code

```java
import javax.sql.*;  
import java.sql.*;  
import com.microsoft.sqlserver.jdbc.*;  

public class UnWrapTest {  
   public static void main(String[] args) {  
      // This is a test.  This DataSource object could be something from an appserver
      // which has wrapped the real SQLServerDataSource with its own wrapper  
      SQLServerDataSource ds = new SQLServerDataSource();  
      checkSendStringParametersAsUnicode(ds);  
   }  

   // Unwrap to the ISQLServerDataSource interface to access the getSendStringParametersAsUnicode function  
   static void checkSendStringParametersAsUnicode(DataSource ds) {  
      try {  
         final ISQLServerDataSource sqlServerDataSource = ds.unwrap(ISQLServerDataSource.class);  
         boolean sendStringParametersAsUnicode = sqlServerDataSource.getSendStringParametersAsUnicode();  

         System.out.println("Send string as parameter value is:-" + sendStringParametersAsUnicode);  

      } catch (SQLException sqlE) {  
         System.out.println("Exception:-" + sqlE);  
      }  
   }  
}  
```

## <a name="see-also"></a>Weitere Informationen

[Grundlegendes zu den Datentypen in JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)
