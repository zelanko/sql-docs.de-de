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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 11378d51cb6d88858ebba069dba161dbbb494f27
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "69028401"
---
# <a name="connecting-and-retrieving-data"></a>Verbinden mit und Abrufen von Daten

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Bei der Arbeit mit dem [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] gibt es zwei primäre Methoden, um eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank herzustellen. Eine Methode besteht darin, die Verbindungseigenschaften in der Verbindungs-URL festzulegen und anschließend die getConnection-Methode der DriverManager-Klasse aufzurufen, um ein [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt zurückzugeben.  
  
> [!NOTE]  
> Eine Liste der vom JDBC-Treiber unterstützten Verbindungseigenschaften finden Sie unter [Festlegen von Verbindungseigenschaften](../../../connect/jdbc/setting-the-connection-properties.md).  
  
Bei der zweiten Methode werden die Verbindungseigenschaften mithilfe von setter-Methoden der [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Klasse festgelegt. Anschließend wird die [getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)-Methode aufgerufen, um ein SQLServerConnection-Objekt zurückzugeben.  
  
Die Themen in diesem Abschnitt beschreiben die verschiedenen Möglichkeiten zum Herstellen einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank sowie die verschiedenen Verfahren zum Abrufen von Daten.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Verbindungs-URL – Beispiel](../../../connect/jdbc/code-samples/connection-url-sample.md)|Beschreibt die Verwendung einer Verbindungs-URL, um eine Verbindung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] herzustellen, und den anschließenden Abruf von Daten mit einer SQL-Anweisung.|  
|[Beispiel für Datenquellen](../../../connect/jdbc/code-samples/data-source-sample.md)|Beschreibt die Verwendung einer Datenquelle, um eine Verbindung zu SQL Server herzustellen und Daten anschließend mit einer gespeicherten Prozedur abzurufen.|  
  
## <a name="see-also"></a>Weitere Informationen

[Beispiele für JDBC-Treiberanwendungen](../../jdbc/code-samples/sample-jdbc-driver-applications.md)
  
