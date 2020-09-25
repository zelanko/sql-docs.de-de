---
title: Verwenden von Anweisungen mit SQL
description: Hier finden Sie eine Übersicht zur Verwendung der verschiedenen Typen von SQL-Anweisungen mit dem Microsoft JDBC-Treiber für SQL Server.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: fe28f48a-e1bc-48ff-a5e7-c24cd6e5ecc7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 49ab0f6367353847bdf3a9e0a7aff13975b4d711
ms.sourcegitcommit: 129f8574eba201eb6ade1f1620c6b80dfe63b331
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2020
ms.locfileid: "87435288"
---
# <a name="using-statements-with-sql"></a>Verwenden von Anweisungen mit SQL

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Wenn Sie Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank mit [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] und Inline-SQL-Anweisungen verarbeiten, können Sie verschiedenen Klassen verwenden. Die verwendete Klasse hängt vom Typ der SQL-Anweisung ab, die ausgeführt werden soll.  
  
Wenn die SQL-Anweisung keine IN-Parameter enthält, verwenden Sie die [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse. Wenn IN-Parameter vorhanden sind, verwenden Sie die [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Klasse.  
  
> [!NOTE]  
> Wenn Sie SQL-Anweisungen verwenden müssen, die IN- und OUT-Parameter enthalten, müssen Sie diese als gespeicherte Prozeduren implementieren und mit der [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klasse aufrufen. Weitere Informationen zur Verwendung von gespeicherten Prozeduren finden Sie unter [Verwenden von Anweisungen mit gespeicherten Prozeduren](../../connect/jdbc/using-statements-with-stored-procedures.md).  
  
Die folgenden Abschnitte enthalten Beschreibungen der verschiedenen Szenarios für die Arbeit mit Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank mit SQL-Anweisungen.  

## <a name="in-this-section"></a>In diesem Abschnitt  

| Thema                                                                                                                        | BESCHREIBUNG                                                       |
| ---------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| [Verwenden von SQL-Anweisungen ohne Parameter](../../connect/jdbc/using-an-sql-statement-with-no-parameters.md)                 | Beschreibt die Verwendung von SQL-Anweisungen, die keine Parameter enthalten.   |
| [Verwenden von SQL-Anweisungen mit Parametern](../../connect/jdbc/using-an-sql-statement-with-parameters.md)                       | Beschreibt die Verwendung von SQL-Anweisungen, die Parameter enthalten.      |
| [Ändern von Datenbankobjekten mit SQL-Anweisungen](../../connect/jdbc/using-an-sql-statement-to-modify-database-objects.md) | Beschreibt die Verwendung von SQL-Anweisungen, um Datenbankobjekte zu ändern.   |
| [Ändern von Daten mit SQL-Anweisungen](../../connect/jdbc/using-an-sql-statement-to-modify-data.md)                         | Beschreibt die Verwendung von SQL-Anweisungen, um Daten in einer Datenbank zu ändern. |
  
## <a name="see-also"></a>Weitere Informationen:

[Verwenden von Anweisungen mit dem JDBC-Treiber](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
