---
title: Abrufen der Treiberversion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5e241d72-16da-4ada-ac67-e6308394108f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1a1c5c6d4dcc3a5bd5acaac37ffdcdadc184e497
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924658"
---
# <a name="getting-the-driver-version"></a>Abrufen der Treiberversion
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Die installierte Version von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] kann wie folgt ermittelt werden:  
  
-   Rufen Sie die [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)-Methoden [getDriverMajorVersion](../../connect/jdbc/reference/getdrivermajorversion-method-sqlserverdatabasemetadata.md), [getDriverMinorVersion](../../connect/jdbc/reference/getdriverminorversion-method-sqlserverdatabasemetadata.md) oder [getDriverVersion](../../connect/jdbc/reference/getdriverversion-method-sqlserverdatabasemetadata.md). auf.  
  
-   Die Version wird in der Datei readme.txt für das Produkt angezeigt.  
  
 Außerdem kann der JDBC-Treibername mit dem [getDriverName](../../connect/jdbc/reference/getdrivername-method-sqlserverdatabasemetadata.md)-Methodenaufruf für die SQLServerDatabaseMetaData-Klasse zurückgegeben werden. Dabei wird z. B. „Microsoft JDBC-Treiber 6.4 für SQL Server“ zurückgegeben.  
  
 Im Folgenden wird ein Beispiel für die Ausgabe von Aufrufen der Methoden in der SQLServerDatabaseMetaData-Klasse bereitgestellt:  
  
 `getDriverName = Microsoft JDBC Driver 6.4 for SQL Server`  
  
 `getDriverMajorVersion = 6`  
  
 `getDriverMinorVersion = 4`  
  
 `getDriverVersion = 6.4.` *xxx.x*  
  
 Dabei ist "xxx.x" die abschließende Versionsnummer.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Diagnostizieren von Problemen mit dem JDBC-Treiber](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
