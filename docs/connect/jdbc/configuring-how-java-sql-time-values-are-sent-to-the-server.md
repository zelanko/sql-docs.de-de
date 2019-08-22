---
title: Konfigurieren der Vorgehensweise zum Senden von java.sql.Time-Werten an den Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 07eb00dd-621a-46f9-a5a5-8cab4d6058b5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8fe6969d51834d0798a530b9cc9926af1b27fec2
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028229"
---
# <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Konfigurieren der Art und Weise, wie java.sql.Time-Werte an den Server gesendet werden
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Wenn Sie ein java.sql.Time-Objekt oder den java.sql.Types.TIME-JDBC-Typ zum Festlegen eines Parameters verwenden, können Sie konfigurieren, wie der java.sql.Time-Wert an den Server gesendet wird: als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **time**-Type oder als **datetime**-Typ.  
  
 Dies trifft zu, wenn eine der folgenden Methoden verwendet wird:  
  
-   [SQLServerCallableStatement.registerOutParameter(int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int.md)  
  
-   [SQLServerCallableStatement.registerOutParameter(int, int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int-int.md)  
  
-   [SQLServerCallableStatement.setTime](../../connect/jdbc/reference/settime-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setTime](../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)  
  
-   [SQLServerCallableStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)  
  
 Verwenden Sie die **sendTimeAsDatetime**-Verbindungseigenschaft, um die Art und Weise zu konfigurieren, auf die der java.sql.Time-Wert gesendet wird. Weitere Informationen zum Festlegen der Verbindungseigenschaften finden Sie unter [Setting the Connection Properties (Festlegen von Verbindungseigenschaften)](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Der Wert der Verbindungseigenschaft **sendTimeAsDatetime** kann mit [SQLServerDataSource.setSendTimeAsDatetime](../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) geändert werden.  
  
 Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor unterstützen den **Time-Datentyp** nicht, sodass Anwendungen, die Java. SQL. Time verwenden, in der Regel Java. SQL. Time-Werte als **DateTime** oder [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] **smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen.  
  
 Wenn Sie beim Arbeiten mit Java. SQL. Time-Werten die Datentypen **DateTime** und **smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwenden möchten, legen Sie die **sendtimeasdatetime** -Verbindungs Eigenschaft auf **true**fest. Wenn Sie beim Arbeiten mit Java. SQL. Time-Werten den Datentyp " **time** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] " verwenden möchten, sollten Sie die **sendtimeasdatetime** -Verbindungs Eigenschaft auf " **false**" festlegen.  
  
 Wenn Sie ausschließlich java.sql.Time-Werte in einen Parameter senden, deren Datentyp ebenfalls das Datum speichern kann, unterscheiden sich die Standarddaten je nachdem, ob der java.sql.Time-Wert als **datetime**- (01.01.1970) oder **time**-Wert (01.01.1900) gesendet wird. Weitere Informationen zu Datenkonvertierungen beim Senden von Daten an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter [Verwenden von Datums- und Zeitdaten](https://go.microsoft.com/fwlink/?LinkID=145211).  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] JDBC Driver 3,0 ist **sendtimeasdatetime** standardmäßig auf true fest. In einem künftigen Release wird die Verbindungseigenschaft **sendTimeAsDatetime** möglicherweise standardmäßig auf FALSE festgelegt.  
  
 Gehen Sie wie folgt vor, um zu gewährleisten, dass die Anwendung unabhängig vom Standardwert der Verbindungseigenschaft **sendTimeAsDatetime** weiterhin funktioniert:  
  
-   Verwenden Sie java.sql.Time, wenn Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp **time** verwenden.  
  
-   Verwenden Sie Java. SQL. Timestamp, wenn Sie mit den Datentypen **DateTime**, **smalldatetime**und **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] arbeiten.  
  
Sendtimeasdatetime muss für verschlüsselte Spalten den Wert false aufweisen, da verschlüsselte Spalten die Konvertierung von Time in DateTime nicht unterstützen. Beginnend mit dem Microsoft JDBC-Treiber 6,0 für SQL Server verfügt die SQLServerConnection-Klasse über die folgenden beiden Methoden, um den Wert der sendtimeasdatetime-Eigenschaft festzulegen/zu erhalten.

```java
  public boolean getSendTimeAsDatetime()
  public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)
```
  
## <a name="see-also"></a>Siehe auch
 [Grundlegendes zu den Datentypen des JDBC-Treibers](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
