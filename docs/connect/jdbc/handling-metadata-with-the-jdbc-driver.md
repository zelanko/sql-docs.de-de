---
title: Verarbeiten von Metadaten mit dem JDBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5cfb35d4-ddcd-40a2-8091-f29cddc32552
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0176e1da9a64e4ed32ba6989496178f5f9741193
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "69028024"
---
# <a name="handling-metadata-with-the-jdbc-driver"></a>Verarbeiten von Metadaten mit dem JDBC-Treiber
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] bietet verschiedene Möglichkeiten zum Verarbeiten von Metadaten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank. Mit dem JDBC-Treiber können Metadaten zur Datenbank, zu einem Resultset oder zu Parametern abgerufen werden.  
  
 Der JDBC-Treiber umfasst drei Klassen zum Abrufen von Metadaten aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank:  
  
-   [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) gibt Informationen über die zurzeit verbundene Datenbank zurück.  
  
-   [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) gibt Informationen über das Resultset zurück.  
  
-   [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md) gibt Informationen über die Parameter vorbereiteter und aufrufbarer Anweisungen zurück.  
  
 In diesem Abschnitt wird beschrieben, wie Sie mithilfe der drei Metadatenklassen in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank Metadaten verarbeiten können.  
  
> [!NOTE]  
>  Die in diesem Abschnitt behandelten Metadatenmethoden wirken sich im Allgemeinen erheblich auf die Leistung der Anwendung aus, sodass deren Verwendung sorgfältig abgewägt werden muss.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Verwenden von Datenbankmetadaten](../../connect/jdbc/using-database-metadata.md)|Beschreibt das Abrufen von Metadateninformationen über die zurzeit verbundene Datenbank.|  
|[Verwenden von Resultsetmetadaten](../../connect/jdbc/using-result-set-metadata.md)|Beschreibt das Abrufen von Metadateninformationen über das aktuelle Resultset.|  
|[Verwenden von Parametermetadaten](../../connect/jdbc/using-parameter-metadata.md)|Beschreibt das Abrufen von Metadateninformationen über die Parameter vorbereiteter und aufrufbarer Anweisungen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über den JDBC-Treiber](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
