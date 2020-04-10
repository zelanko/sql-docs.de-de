---
title: Verbinden und Abrufen von Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 991cdbf97c03fc1e8734aa412662a43135a8f331
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922496"
---
# <a name="connecting-and-retrieving-data"></a>Verbinden mit und Abrufen von Daten

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Bei der Arbeit mit dem [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] gibt es zwei primäre Methoden, um eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank herzustellen. Eine Methode besteht darin, die Verbindungseigenschaften in der Verbindungs-URL festzulegen und anschließend die getConnection-Methode der DriverManager-Klasse aufzurufen, um ein [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt zurückzugeben.  
  
> [!NOTE]  
> Eine Liste der vom JDBC-Treiber unterstützten Verbindungseigenschaften finden Sie unter [Festlegen von Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md).  
  
Bei der zweiten Methode werden die Verbindungseigenschaften mithilfe von setter-Methoden der [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)-Klasse festgelegt. Anschließend wird die [getConnection](../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)-Methode aufgerufen, um ein SQLServerConnection-Objekt zurückzugeben.  
  
Die Themen in diesem Abschnitt beschreiben die verschiedenen Möglichkeiten zum Herstellen einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank sowie die verschiedenen Verfahren zum Abrufen von Daten.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
| Thema                                                                | BESCHREIBUNG                                                                                                                                                   |
| -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Verbindungs-URL – Beispiel](../../connect/jdbc/connection-url-sample.md) | Beschreibt die Verwendung einer Verbindungs-URL, um eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herzustellen, und den anschließenden Abruf von Daten mit einer SQL-Anweisung. |
| [Beispiel für Datenquellen](../../connect/jdbc/data-source-sample.md)       | Beschreibt die Verwendung einer Datenquelle, um eine Verbindung zu SQL Server herzustellen und Daten anschließend mit einer gespeicherten Prozedur abzurufen.                                                 |
  
## <a name="see-also"></a>Weitere Informationen

[Beispiele für JDBC-Treiberanwendungen](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
