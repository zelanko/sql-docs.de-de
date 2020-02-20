---
title: Verwenden mehrerer Resultsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ab6a3cfa-073b-44e9-afca-a8675cfe5fd1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 802ade7a34eb5c5174efc35032587f801ef12179
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "69026275"
---
# <a name="using-multiple-result-sets"></a>Verwenden von mehreren Resultsets

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Bei der Arbeit mit Inline-SQL-Prozeduren oder gespeicherten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozeduren, die mehrere Resultsets zurückgeben, stellt [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] die Methode [getResultSet](../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md) in der Klasse [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) bereit, um die einzelnen zurückgegebenen Datensätze abzurufen. Beim Ausführen einer Anweisung, die mehrere Resultsets zurückgibt, können Sie darüber hinaus die Methode [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) der SQLServerStatement-Klasse verwenden, da ein **boolescher** Wert zurückgegeben wird, der angibt, ob es sich bei dem zurückgegebenen Wert um ein Resultset oder eine Updatezählung handelt.

Wenn die Methode „execute“ **TRUE** zurückgibt, wurde von der ausgeführten Anweisung mindestens ein Resultset zurückgegeben. Sie können die Methode „getResultSet“ aufrufen, um auf das erste Resultset zuzugreifen. Um zu ermitteln, ob weitere Resultsets verfügbar sind, können Sie die Methode [getMoreResults](../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md) aufrufen, die den **booleschen** Wert **TRUE** zurückgibt, falls weitere Resultsets verfügbar sind. Wenn mehr Resultsets verfügbar sind, können Sie erneut die Methode „getResultSet“ aufrufen, um darauf zuzugreifen, und den Prozess fortsetzen, bis alle Resultsets verarbeitet wurden. Wenn die getMoreResults-Methode **FALSE** zurückgibt, sind keine weiteren Resultsets mehr für die Verarbeitung vorhanden.

Wenn die Methode „execute“ **FALSE** zurückgibt, wurde von der ausgeführten Anweisung ein Updatezählwert zurückgegeben, der durch Aufruf der Methode [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) abgerufen werden kann.

> [!NOTE]  
> Weitere Informationen zu aktualisierten Zählerwerten finden Sie unter [Verwenden von gespeicherten Prozedur mit aktualisierten Zählerwerten](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md).

Im folgenden Beispiel werden eine offene Verbindung mit der Beispieldatenbank [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] an die Funktion übergeben und eine SQL-Anweisung erstellt, die bei der Ausführung zwei Resultsets zurückgibt:

[!code[JDBC#UsingMultipleResultSets1](../../connect/jdbc/codesnippet/Java/using-multiple-result-sets_1.java)]

In diesem Fall ist bekannt, dass zwei Resultsets zurückgegeben werden. Der Code ist jedoch so geschrieben, dass alle Resultsets verarbeitet werden, wenn die Anzahl der zurückgegebenen Resultsets unbekannt ist, wie z. B. beim Aufrufen einer gespeicherten Prozedur. Ein Beispiel für den Aufruf einer gespeicherten Prozedur, die mehrere Resultsets sowie Updatewerte zurückgibt, finden Sie unter [Verarbeiten komplexer Anweisungen](../../connect/jdbc/handling-complex-statements.md).

> [!NOTE]  
> Wenn Sie die getMoreResults-Methode der SQLServerStatement-Klasse aufrufen, wird das zuvor zurückgegebene Resultset implizit geschlossen.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Anweisungen mit dem JDBC-Treiber](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)
