---
title: Binden von Parametern anhand des Namens (benannte Parameter) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- named parameters [ODBC]
- binding parameters by name [ODBC]
ms.assetid: e2c3da5a-6c10-4dd5-acf9-e951eea71a6b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a1e214f50488c4600ed39f76e91618cc5ce53de4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306371"
---
# <a name="binding-parameters-by-name-named-parameters"></a>Binden von Parametern anhand des Namens (benannte Parameter)
Bestimmte DBMSs ermöglichen es einer Anwendung, die Parameter für eine gespeicherte Prozedur anstelle der Position im Prozedur aufzurufen, sondern anhand ihres Namens anzugeben. Solche Parameter werden als *benannte Parameter*bezeichnet. ODBC unterstützt die Verwendung benannter Parameter. In ODBC werden benannte Parameter nur in Aufrufen von gespeicherten Prozeduren verwendet und können nicht in anderen SQL-Anweisungen verwendet werden.  
  
 Der Treiber prüft den Wert des SQL_DESC_UNNAMED Felds der IPD, um zu bestimmen, ob benannte Parameter verwendet werden. Wenn SQL_DESC_UNNAMED nicht auf SQL_UNNAMED festgelegt ist, verwendet der Treiber den Namen im SQL_DESC_NAME-Feld der IPD, um den Parameter zu identifizieren. Zum Binden des Parameters kann eine Anwendung **SQLBindParameter** aufrufen, um die Parameterinformationen anzugeben, und anschließend **SQLSetDescField** aufrufen, um das SQL_DESC_NAME-Feld der IPD festzulegen. Wenn benannte Parameter verwendet werden, ist die Reihenfolge des Parameters im Prozedur aufrufen nicht wichtig, und die Datensatznummer des Parameters wird ignoriert.  
  
 Der Unterschied zwischen unbenannten Parametern und benannten Parametern liegt in der Beziehung zwischen der Datensatznummer des Deskriptors und der Parameter Nummer in der Prozedur. Wenn unbenannte Parameter verwendet werden, ist die erste Parameter Markierung mit dem ersten Datensatz im Parameter Deskriptor verknüpft, der wiederum mit dem ersten Parameter (in der Erstellungs Reihenfolge) im-Prozedur aufrufen verknüpft ist. Wenn benannte Parameter verwendet werden, ist die erste Parameter Markierung weiterhin mit dem ersten Datensatz des Parameter Deskriptors verknüpft, aber die Beziehung zwischen der Datensatznummer des Deskriptors und der Parameter Nummer in der Prozedur ist nicht mehr vorhanden. Benannte Parameter verwenden nicht die Zuordnung der Deskriptordatensatz-Nummer zur Prozedur Parameter Position; Stattdessen wird der Name des deskriptoreinbilds dem Prozedur Parameternamen zugeordnet.  
  
> [!NOTE]  
>  Wenn die automatische Auffüllung der IPD aktiviert ist, füllt der Treiber den Deskriptor so auf, dass die Reihenfolge der deskriptordaten Sätze der Reihenfolge der Parameter in der Prozedur Definition entspricht, auch wenn benannte Parameter verwendet werden.  
  
 Wenn ein benannter Parameter verwendet wird, müssen alle Parameter benannte Parameter sein. Wenn ein beliebiger Parameter kein benannter Parameter ist, werden keine Parameter der Zertifizierungsstelle als Parameter bezeichnet. Wenn eine Mischung aus benannten Parametern und unbenannten Parametern vorhanden wäre, wäre das Verhalten Treiber abhängig.  
  
 Angenommen, als Beispiel für benannte Parameter wurde eine gespeicherte Prozedur SQL Server wie folgt definiert:  
  
```  
CREATE PROCEDURE test @title_id int = 1, @quote char(30) AS <blah>  
```  
  
 In diesem Verfahren hat der erste Parameter @title_idden Standardwert 1. Eine Anwendung kann den folgenden Code verwenden, um diese Prozedur so aufzurufen, dass nur ein dynamischer Parameter angegeben wird. Dieser Parameter ist ein benannter Parameter mit dem\@Namen "Quote".  
  
```  
// Prepare the procedure invocation statement.  
SQLPrepare(hstmt, "{call test(?)}", SQL_NTS);  
  
// Populate record 1 of ipd.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR,  
                  30, 0, szQuote, 0, &cbValue);  
  
// Get ipd handle and set the SQL_DESC_NAMED and SQL_DESC_UNNAMED fields  
// for record #1.  
SQLGetStmtAttr(hstmt, SQL_ATTR_IMP_PARAM_DESC, &hIpd, 0, 0);  
SQLSetDescField(hIpd, 1, SQL_DESC_NAME, "@quote", SQL_NTS);  
  
// Assuming that szQuote has been appropriately initialized,  
// execute.  
SQLExecute(hstmt);  
```
