---
title: Bindungsparameter nach Name (Benannte Parameter) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306371"
---
# <a name="binding-parameters-by-name-named-parameters"></a>Binden von Parametern anhand des Namens (benannte Parameter)
Bestimmte DBMS ermöglichen es einer Anwendung, die Parameter für eine gespeicherte Prozedur nach Namen und nicht nach Position im Prozeduraufruf anzugeben. Solche Parameter werden *als benannte Parameter*bezeichnet. ODBC unterstützt die Verwendung benannter Parameter. In ODBC werden benannte Parameter nur in Aufrufen gespeicherter Prozeduren verwendet und können nicht in anderen SQL-Anweisungen verwendet werden.  
  
 Der Treiber überprüft den Wert des feldes SQL_DESC_UNNAMED der IPD, um festzustellen, ob benannte Parameter verwendet werden. Wenn SQL_DESC_UNNAMED nicht auf SQL_UNNAMED festgelegt ist, verwendet der Treiber den Namen im feld SQL_DESC_NAME der IPD, um den Parameter zu identifizieren. Um den Parameter zu binden, kann eine Anwendung **SQLBindParameter** aufrufen, um die Parameterinformationen anzugeben, und dann **SQLSetDescField** aufrufen, um das SQL_DESC_NAME Feld der IPD festzulegen. Wenn benannte Parameter verwendet werden, ist die Reihenfolge des Parameters im Prozeduraufruf nicht wichtig, und die Datensatznummer des Parameters wird ignoriert.  
  
 Die Differenz zwischen unbenannten Parametern und benannten Parametern liegt in der Beziehung zwischen der Datensatznummer des Deskriptors und der Parameternummer in der Prozedur. Wenn unbenannte Parameter verwendet werden, bezieht sich die erste Parametermarkierung auf den ersten Datensatz im Parameterdeskriptor, der wiederum mit dem ersten Parameter (in Erstellungsreihenfolge) im Prozeduraufruf verknüpft ist. Wenn benannte Parameter verwendet werden, ist die erste Parametermarkierung immer noch mit dem ersten Datensatz des Parameterdeskriptors verknüpft, aber die Beziehung zwischen der Datensatznummer des Deskriptors und der Parameternummer in der Prozedur ist nicht mehr vorhanden. Benannte Parameter verwenden nicht die Zuordnung der Deskriptor-Datensatznummer zur Prozedurparameterposition. Stattdessen wird der Name des Deskriptordatensatzes dem Prozedurparameternamen zugeordnet.  
  
> [!NOTE]  
>  Wenn die automatische Auffüllung der IPD aktiviert ist, füllt der Treiber den Deskriptor so aus, dass die Reihenfolge der Deskriptordatensätze mit der Reihenfolge der Parameter in der Prozedurdefinition übereinstimmt, auch wenn benannte Parameter verwendet werden.  
  
 Wenn ein benannter Parameter verwendet wird, müssen alle Parameter als Parameter bezeichnet werden. Wenn ein Parameter kein benannter Parameter ist, wird keiner der Parameter ca als Parameter benannt. Wenn es eine Mischung aus benannten Parametern und unbenannten Parametern gäbe, wäre das Verhalten treiberabhängig.  
  
 Als Beispiel für benannte Parameter nehmen wir an, dass eine gespeicherte SQL Server-Prozedur wie folgt definiert wurde:  
  
```  
CREATE PROCEDURE test @title_id int = 1, @quote char(30) AS <blah>  
```  
  
 In dieser Prozedur hat @title_idder erste Parameter , den Standardwert 1. Eine Anwendung kann den folgenden Code verwenden, um diese Prozedur so aufzurufen, dass sie nur einen dynamischen Parameter angibt. Dieser Parameter ist ein benannter\@Parameter mit dem Namen "quote".  
  
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
