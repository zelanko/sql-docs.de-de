---
title: Abrufen der Treiberversion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5e241d72-16da-4ada-ac67-e6308394108f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7abc69edd0d49264a62ea0c3f65a60b58549d105
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47774218"
---
# <a name="getting-the-driver-version"></a>Abrufen der Treiberversion
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Die installierte Version von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] kann wie folgt ermittelt werden:  
  
-   Rufen Sie die [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)-Methoden [getDriverMajorVersion](../../connect/jdbc/reference/getdrivermajorversion-method-sqlserverdatabasemetadata.md), [getDriverMinorVersion](../../connect/jdbc/reference/getdriverminorversion-method-sqlserverdatabasemetadata.md) oder [getDriverVersion](../../connect/jdbc/reference/getdriverversion-method-sqlserverdatabasemetadata.md). auf.  
  
-   Die Version wird in der Datei readme.txt für das Produkt angezeigt.  
  
 Außerdem kann der JDBC-Treibername mit dem [getDriverName](../../connect/jdbc/reference/getdrivername-method-sqlserverdatabasemetadata.md)-Methodenaufruf für die SQLServerDatabaseMetaData-Klasse zurückgegeben werden. Dabei wird z. B. „Microsoft JDBC-Treiber 6.4 für SQL Server“ zurückgegeben.  
  
 Im folgenden finden ein Beispiel der Ausgabe von Aufrufen an die Methoden der SQLServerDatabaseMetaData-Klasse:  
  
 `getDriverName = Microsoft JDBC Driver 6.4 for SQL Server`  
  
 `getDriverMajorVersion = 6`  
  
 `getDriverMinorVersion = 4`  
  
 `getDriverVersion = 6.4.` *xxx.x*  
  
 Dabei ist "xxx.x" die abschließende Versionsnummer.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Diagnostizieren von Problemen mit dem JDBC-Treiber](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
