---
title: Verwenden mehrerer Resultsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ab6a3cfa-073b-44e9-afca-a8675cfe5fd1
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e17da2ae58d76268ec962c007b0fd81b5fc06d60
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662402"
---
# <a name="using-multiple-result-sets"></a>Verwenden von mehreren Resultsets

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Bei der Arbeit mit Inline-SQL-Prozeduren oder gespeicherten [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Prozeduren, die mehrere Resultsets zurückgeben, stellt [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] die Methode [getResultSet](../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md) in der Klasse [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) bereit, um die einzelnen zurückgegebenen Datensätze abzurufen. Beim Ausführen einer Anweisung, die mehrere Resultsets zurückgibt, können Sie darüber hinaus die Methode [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) der SQLServerStatement-Klasse verwenden, da ein **boolescher** Wert zurückgegeben wird, der angibt, ob es sich bei dem zurückgegebenen Wert um ein Resultset oder eine Updatezählung handelt.

Wenn die Methode „execute“ **TRUE** zurückgibt, wurde von der ausgeführten Anweisung mindestens ein Resultset zurückgegeben. Sie können die Methode „getResultSet“ aufrufen, um auf das erste Resultset zuzugreifen. Um zu ermitteln, ob weitere Resultsets verfügbar sind, können Sie die Methode [getMoreResults](../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md) aufrufen, die den **booleschen** Wert **TRUE** zurückgibt, falls weitere Resultsets verfügbar sind. Wenn mehr Resultsets verfügbar sind, können Sie erneut die Methode „getResultSet“ aufrufen, um darauf zuzugreifen, und den Prozess fortsetzen, bis alle Resultsets verarbeitet wurden. Wenn Sie die GetMoreResults-Methode gibt **"false"**, es sind keine weiteren Resultsets zu verarbeiten.

Wenn die Methode „execute“ **FALSE** zurückgibt, wurde von der ausgeführten Anweisung ein Updatezählwert zurückgegeben, der durch Aufruf der Methode [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) abgerufen werden kann.

> [!NOTE]  
> Weitere Informationen zu updatezählungen finden Sie unter [mithilfe einer gespeicherten Prozedur mit einer Anzahl aktualisieren](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md).

Im folgenden Beispiel werden eine offene Verbindung mit der Beispieldatenbank [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] an die Funktion übergeben und eine SQL-Anweisung erstellt, die bei der Ausführung zwei Resultsets zurückgibt:

[!code[JDBC#UsingMultipleResultSets1](../../connect/jdbc/codesnippet/Java/using-multiple-result-sets_1.java)]

In diesem Fall ist bekannt, dass zwei Resultsets zurückgegeben werden. Der Code ist jedoch so geschrieben, dass alle Resultsets verarbeitet werden, wenn die Anzahl der zurückgegebenen Resultsets unbekannt ist, wie z. B. beim Aufrufen einer gespeicherten Prozedur. Ein Beispiel für den Aufruf einer gespeicherten Prozedur, die mehrere Resultsets sowie Updatewerte zurückgibt, finden Sie unter [Verarbeiten komplexer Anweisungen](../../connect/jdbc/handling-complex-statements.md).

> [!NOTE]  
> Wenn Sie die GetMoreResults-Methode der SQLServerStatement-Klasse aufrufen, wird das zuvor zurückgegebene Resultset implizit geschlossen.

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Verwenden von Anweisungen mit dem JDBC-Treiber](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)
