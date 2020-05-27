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
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "69028229"
---
# <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Konfigurieren der Art und Weise, wie java.sql.Time-Werte an den Server gesendet werden
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Wenn Sie ein java.sql.Time-Objekt oder den java.sql.Types.TIME-JDBC-Typ zum Festlegen eines Parameters verwenden, können Sie konfigurieren, wie der java.sql.Time-Wert an den Server gesendet wird: als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]time **- oder als** datetime **-** -Typ.  
  
 Dies trifft zu, wenn eine der folgenden Methoden verwendet wird:  
  
-   [SQLServerCallableStatement.registerOutParameter(int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int.md)  
  
-   [SQLServerCallableStatement.registerOutParameter(int, int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int-int.md)  
  
-   [SQLServerCallableStatement.setTime](../../connect/jdbc/reference/settime-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setTime](../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)  
  
-   [SQLServerCallableStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)  
  
 Verwenden Sie die **sendTimeAsDatetime**-Verbindungseigenschaft, um die Art und Weise zu konfigurieren, auf die der java.sql.Time-Wert gesendet wird. Weitere Informationen zum Festlegen der Verbindungseigenschaften finden Sie unter [Setting the Connection Properties (Festlegen von Verbindungseigenschaften)](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Der Wert der Verbindungseigenschaft **sendTimeAsDatetime** kann mit [SQLServerDataSource.setSendTimeAsDatetime](../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) geändert werden.  
  
 In den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Versionen vor [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] wurde der **time**-Datentyp nicht unterstützt, sodass Anwendungen, die java.sql.Time verwenden, java.sql.Time-Werte in der Regel entweder als **datetime**- oder -**smalldatetime**-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen speichern.  
  
 Wenn Sie beim Arbeiten mit java.sql.Time-Werten die **datetime**- und **smalldatetime**-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen verwenden möchten, sollten Sie die Verbindungseigenschaft **sendTimeAsDatetime** auf **TRUE** festlegen. Wenn Sie beim Arbeiten mit java.sql.Time-Werten den **time**-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp verwenden möchten, sollten Sie die Verbindungseigenschaft **sendTimeAsDatetime** auf **FALSE** festlegen.  
  
 Wenn Sie ausschließlich java.sql.Time-Werte in einen Parameter senden, deren Datentyp ebenfalls das Datum speichern kann, unterscheiden sich die Standarddaten je nachdem, ob der java.sql.Time-Wert als **datetime**- (01.01.1970) oder **time**-Wert (01.01.1900) gesendet wird. Weitere Informationen zu Datenkonvertierungen beim Senden von Daten an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter [Verwenden von Datums- und Zeitdaten](https://go.microsoft.com/fwlink/?LinkID=145211).  
  
 Im JDBC-Treiber 3.0 für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist **sendTimeAsDatetime** standardmäßig auf TRUE festgelegt. In einem künftigen Release wird die Verbindungseigenschaft **sendTimeAsDatetime** möglicherweise standardmäßig auf FALSE festgelegt.  
  
 Gehen Sie wie folgt vor, um zu gewährleisten, dass die Anwendung unabhängig vom Standardwert der Verbindungseigenschaft **sendTimeAsDatetime** weiterhin funktioniert:  
  
-   Verwenden Sie java.sql.Time, wenn Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp **time** verwenden.  
  
-   Verwenden Sie java.sql.Timestamp beim Arbeiten mit den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen **datetime**, **smalldatetime** und **datetime2**.  
  
SendTimeAsDatetime muss für verschlüsselte Spalten den Wert FALSE aufweisen, da verschlüsselte Spalten die Konvertierung von time in datetime nicht unterstützen. Beginnend mit Microsoft JDBC-Treiber 6.0 für SQL Server verfügt die SQLServerConnection-Klasse über die folgenden beiden Methoden, um den Wert der sendTimeAsDatetime-Eigenschaft festzulegen bzw. abzurufen.

```java
  public boolean getSendTimeAsDatetime()
  public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)
```
  
## <a name="see-also"></a>Weitere Informationen
 [Grundlegendes zu den Datentypen des JDBC-Treibers](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
