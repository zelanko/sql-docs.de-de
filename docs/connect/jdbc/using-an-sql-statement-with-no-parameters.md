---
title: Verwenden einer SQL-Anweisung ohne Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4b0728bd-059b-4b71-895c-999335bc7427
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce923add20ff96ea63caea0073c5cfb9c6235253
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39661682"
---
# <a name="using-an-sql-statement-with-no-parameters"></a>Verwenden von SQL-Anweisungen ohne Parameter

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Wenn Sie Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Datenbank mit einer SQL-Anweisung ohne Parameter verarbeiten möchten, können Sie mit der [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)-Methode der [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse ein [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) zurückgeben, das die angeforderten Daten enthält. Sie müssen dazu zuerst mit der [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse ein SQLServerStatement-Objekt erstellen.

Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben, eine SQL-Anweisung wird erstellt und ausgeführt, und die Ergebnisse werden aus dem Resultset gelesen.

[!code[JDBC#UsingSQLWithNoParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_0_1.java)]

Weitere Informationen zur Verwendung von Resultsets finden Sie unter [Verwalten von Resultsets mit dem JDBC-Treiber](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md).

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Verwenden von Anweisungen mit SQL](../../connect/jdbc/using-statements-with-sql.md)
