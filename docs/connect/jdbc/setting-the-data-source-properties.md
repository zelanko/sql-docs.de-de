---
title: Festlegen der Daten von Quelleigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f3363d05-07fc-4bf8-ae5e-2a7a968808ad
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e9957a3273f2e33fea59560c4af30ec0315eea92
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2018
ms.locfileid: "39458024"
---
# <a name="setting-the-data-source-properties"></a>Festlegen der Datenquelleneigenschaften

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Datenquellen bilden den bevorzugten Mechanismus, mit dem in einer Umgebung der Java-Plattform, Enterprise Edition (Java EE) JDBC-Verbindungen erstellt werden. Datenquellen ermöglichen Verbindungen, Poolverbindungen und verteilte Verbindungen, ohne die Verbindungseigenschaften fest im Java-Code codieren zu müssen. Alle Datenquellen für [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] können alle Eigenschaften mit den entsprechenden Setter- oder Getter-Methoden abrufen bzw. festlegen.

Java EE-Produkte wie Anwendungsserver und Servlet-/JSP-Engines lassen normalerweise die Konfiguration von Datenquellen für den Datenbankzugriff zu. Alle im Artikel [Festlegen von Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md) aufgeführten Eigenschaften können überall angegeben werden, wo die Konfiguration die Eingabe einer Eigenschaft als Eigenschaft-Wert-Paar zulässt.

Weitere Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Datenquellen finden Sie unter der [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)-Klasse. Ein Beispiel dafür, wie mit der SQLServerDataSource-Klasse, zum Herstellen einer Verbindung mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] finden Sie unter [-Datenquellenbeispiel](../../connect/jdbc/data-source-sample.md).

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Verbinden von SQL Server mit dem JDBC-Treiber](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
