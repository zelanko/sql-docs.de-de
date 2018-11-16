---
title: Konfigurieren der Vorgehensweise zum Senden von java.sql.Time-Werten an den Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 07eb00dd-621a-46f9-a5a5-8cab4d6058b5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0f359c66250d11fa01c74567e1faeab3ff064ac
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602250"
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
  
 Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] unterstützen nicht die **Zeit** -Datentyp, damit Anwendungen, die in der Regel mithilfe von java.sql.Time java.sql.Time speichern Werte entweder als **"DateTime"** oder **Smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen.  
  
 Wenn Sie verwenden möchten die **"DateTime"** und **Smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen beim Arbeiten mit java.sql.Time-Werte, die Sie festlegen sollten die **SendTimeAsDatetime** Connection-Eigenschaft, um **"true"**. Wenn Sie verwenden möchten die **Zeit** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp beim Arbeiten mit java.sql.Time-Werte, legen Sie die **SendTimeAsDatetime** -Verbindungseigenschaft auf **"false"**.  
  
 Wenn Sie ausschließlich java.sql.Time-Werte in einen Parameter senden, deren Datentyp ebenfalls das Datum speichern kann, unterscheiden sich die Standarddaten je nachdem, ob der java.sql.Time-Wert als **datetime**- (01.01.1970) oder **time**-Wert (01.01.1900) gesendet wird. Weitere Informationen zu Datenkonvertierungen beim Senden von Daten an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter [Verwenden von Datums- und Zeitdaten](https://go.microsoft.com/fwlink/?LinkID=145211).  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] JDBC Driver 3.0 **SendTimeAsDatetime** ist standardmäßig "true". In einem künftigen Release wird die Verbindungseigenschaft **sendTimeAsDatetime** möglicherweise standardmäßig auf FALSE festgelegt.  
  
 Gehen Sie wie folgt vor, um zu gewährleisten, dass die Anwendung unabhängig vom Standardwert der Verbindungseigenschaft **sendTimeAsDatetime** weiterhin funktioniert:  
  
-   Verwenden Sie java.sql.Time, wenn Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp **time** verwenden.  
  
-   Verwenden Sie java.sql.Timestamp, bei der Arbeit mit der **"DateTime"**, **Smalldatetime**, und **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen.  
  
SendTimeAsDatetime muss "false" für verschlüsselte Spalten sein, wie verschlüsselte Spalten nicht die Konvertierung von Zeit zu "DateTime" unterstützen. Microsoft JDBC-Treiber 6.0 für SQL Server ab, die SQLServerConnection-Klasse verfügt über die folgenden beiden Methoden zum Festlegen/Abrufen von den Wert der Eigenschaft SendTimeAsDatetime.

```java
  public boolean getSendTimeAsDatetime()
  public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)
```
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Grundlegendes zu den Datentypen in JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
