---
title: Verwenden von Parametermetadaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: db2c1957-91c6-4989-a07b-9f8be6d2033a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 80ff8cebcc4141e8363c25f83821cb4924e6c46a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "69026075"
---
# <a name="using-parameter-metadata"></a>Verwenden von Parametermetadaten

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Für die Abfrage der enthaltenen Parameter bei [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)- oder [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Objekten implementiert [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] die [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md)-Klasse. Diese Klasse enthält eine Vielzahl von Feldern und Methoden, die Informationen in der Form eines einzelnen Werts zurückgeben.

Sie können die [getParameterMetaData](../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md)-Methoden der SQLServerPreparedStatement- und SQLServerCallableStatement-Methoden verwenden, um ein SQLServerParameterMetaData-Objekt zu erstellen.

Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben, mit der getParameterMetaData-Methode der SQLServerCallableStatement-Klasse wird ein SQLServerParameterMetaData-Objekt zurückgegeben und dann werden die verschiedenen Methoden des SQLServerParameterMetaData-Objekts dazu genutzt, Informationen zu Typ und Modus der Parameter anzuzeigen, die in der gespeicherten Prozedur „HumanResources.uspUpdateEmployeeHireInfo“ enthalten sind.

[!code[JDBC#UsingParamMetaData1](../../connect/jdbc/codesnippet/Java/using-parameter-metadata_1.java)]  

> [!NOTE]  
> Bei der Verwendung der SQLServerParameterMetaData-Klasse mit Prepared Statements gibt es einige Einschränkungen.
>
> **Mit Microsoft JDBC-Treiber 6.0 (oder höher) für SQL Server:** Bei SQL Server 2008 oder 2008 R2 unterstützt der JDBC-Treiber SELECT-, DELETE-, INSERT- und UPDATE-Anweisungen. Diese Anweisungen dürfen jedoch keine Unterabfragen und/oder Joins enthalten.

Auch MERGE-Abfragen werden bei SQL Server 2008 oder 2008 R2 nicht für die SQLServerParameterMetaData-Klasse unterstützt. Bei SQL Server 2012 und höheren werden Parametermetadaten in komplexen Abfragen unterstützt.

Das Abrufen von Parametermetadaten für verschlüsselte Spalten wird nicht unterstützt. **Mit Microsoft-JDBC-Treiber 4.1 oder 4.2 für SQL Server:** Der JDBC-Treiber unterstützt SELECT-, DELETE-, INSERT- und UPDATE-Anweisungen. Diese Anweisungen dürfen jedoch keine Unterabfragen und/oder Joins enthalten. Auch MERGE-Abfragen werden nicht für die SQLServerParameterMetaData-Klasse unterstützt.
