---
title: Verarbeiten komplexer Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6b807a45-a8b5-4b1c-8b7b-d8175c710ce0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b2b6dd6bb5fb3a0d7b2e9b78dee87f90f05147df
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66781787"
---
# <a name="handling-complex-statements"></a>Verarbeiten komplexer Anweisungen
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Bei Verwendung von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] müssen Sie u. U. komplexe Anweisungen verarbeiten, z. B. Anweisungen, die zur Laufzeit dynamisch generiert werden. Komplexe Anweisungen führen oftmals eine Vielzahl von Tasks aus, wie z. B. Update-, Insert- und Delete-Operationen. Diese Anweisungstypen können auch mehrere Resultsets und Ausgabeparameter zurückgeben. In diesen Situationen kann es vorkommen, dass der Java-Code, der die Anweisungen ausführt, die Typen und die Anzahl der zurückgegebenen Objekte und Daten zunächst nicht kennt.  
  
 Um komplexe Anweisungen effizient auszuführen, umfasst der JDBC-Treiber eine Reihe von Methoden, um die zurückgegebenen Objekte und Daten abzufragen, damit sie in der Anwendung ordnungsgemäß verarbeitet werden können. Der Schlüssel für die Verarbeitung komplexer Anweisungen ist die [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md)-Methode der [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse. Diese Methode gibt eine **booleschen** Wert. Ist der Wert "true", handelt es sich bei dem ersten zurückgegebenen Ergebnis der Anweisungen um ein Resultset. Ist der Wert "false", handelt es sich bei dem ersten zurückgegebenen Ergebnis um eine Updatezählung.  
  
 Wenn Sie den Typ der zurückgegebenen Objekte oder Daten kennen, können Sie diese Daten mit der [getResultSet](../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)-Methode bzw. der [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)-Methode verarbeiten. Um die nächsten Objekte oder Daten zu verarbeiten, die von der komplexen Anweisung zurückgegeben werden, können Sie die [getMoreResults](../../connect/jdbc/reference/getmoreresults-method.md)-Methode aufrufen.  
  
 Im folgenden Beispiel werden eine offene Verbindung zur [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben, eine komplexe Anweisung erstellt, die den Aufruf einer gespeicherten Prozedur mit einer SQL-Anweisung kombiniert, die Anweisungen ausgeführt und dann alle zurückgegebenen Resultsets und Updatezählungen in einer `do`-Schleife verarbeitet.  
  
 [!code[JDBC#HandlingComplexStatements1](../../connect/jdbc/codesnippet/Java/handling-complex-statements_1.java)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Anweisungen mit dem JDBC-Treiber](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
