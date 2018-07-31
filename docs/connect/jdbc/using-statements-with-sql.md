---
title: Verwenden von Anweisungen mit SQL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fe28f48a-e1bc-48ff-a5e7-c24cd6e5ecc7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac74ec1c202341d6de099d97e2b7c719c2f72d27
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37978622"
---
# <a name="using-statements-with-sql"></a>Verwenden von Anweisungen mit SQL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Wenn Sie Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Datenbank mit [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] und Inline-SQL-Anweisungen verarbeiten, können Sie verschiedenen Klassen verwenden. Die verwendete Klasse hängt vom Typ der SQL-Anweisung ab, die ausgeführt werden soll.  
  
 Wenn die SQL-Anweisung keine IN-Parameter enthält, verwenden Sie die [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse. Wenn IN-Parameter vorhanden sind, verwenden Sie die [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Klasse.  
  
> [!NOTE]  
>  Wenn Sie SQL-Anweisungen verwenden müssen, die IN- und OUT-Parameter enthalten, müssen Sie diese als gespeicherte Prozeduren implementieren und mit der [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klasse aufrufen. Weitere Informationen zur Verwendung von gespeicherter Prozeduren finden Sie unter [Using-Anweisungen mit gespeicherten Prozeduren](../../connect/jdbc/using-statements-with-stored-procedures.md).  
  
 Die folgenden Abschnitte enthalten Beschreibungen der verschiedenen Szenarios für die Arbeit mit Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Datenbank mit SQL-Anweisungen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|und Beschreibung|  
|-----------|-----------------|  
|[Verwenden von SQL-Anweisungen ohne Parameter](../../connect/jdbc/using-an-sql-statement-with-no-parameters.md)|Beschreibt die Verwendung von SQL-Anweisungen, die keine Parameter enthalten.|  
|[Verwenden von SQL-Anweisungen mit Parametern](../../connect/jdbc/using-an-sql-statement-with-parameters.md)|Beschreibt die Verwendung von SQL-Anweisungen, die Parameter enthalten.|  
|[Ändern von Datenbankobjekten mit SQL-Anweisungen](../../connect/jdbc/using-an-sql-statement-to-modify-database-objects.md)|Beschreibt die Verwendung von SQL-Anweisungen, um Datenbankobjekte zu ändern.|  
|[Ändern von Daten mit SQL-Anweisungen](../../connect/jdbc/using-an-sql-statement-to-modify-data.md)|Beschreibt die Verwendung von SQL-Anweisungen, um Daten in einer Datenbank zu ändern.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verwenden von Anweisungen mit dem JDBC-Treiber](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
