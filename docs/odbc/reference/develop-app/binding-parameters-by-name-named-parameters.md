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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 68dfb8976312016ee7f2e42fc4fcdecb93fd28cf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199379"
---
# <a name="binding-parameters-by-name-named-parameters"></a>Binden von Parametern anhand des Namens (benannte Parameter)
Bestimmte DBMS ermöglichen eine Anwendung, die Parameter an eine gespeicherte Prozedur nach Namen anstatt anhand der Position im Aufruf Prozedur anzugeben. Solche Parameter heißen *benannte Parameter*. ODBC unterstützt die Verwendung von benannten Parametern. Benannte Parameter werden nur in Aufrufen von gespeicherten Prozeduren verwendet und können nicht in anderen SQL­Anweisungen verwendet werden, in ODBC.  
  
 Der Treiber überprüft den Wert des Felds SQL_DESC_UNNAMED des IPD, zu bestimmen, ob mit dem Namen Parameter verwendet werden. Wenn SQL_DESC_UNNAMED SQL_UNNAMED nicht festgelegt ist, verwendet der Treiber den Namen in SQL_DESC_NAME-Felds des IPD zur Identifizierung des Parameters an. Um den Parameter zu binden, kann eine Anwendung aufrufen **SQLBindParameter** , geben Sie die Parameterinformationen und können Sie **SQLSetDescField** des IPD SQL_DESC_NAME-Felds festgelegt. Wenn benannte Parameter verwendet werden, wird die Reihenfolge der Parameter im Aufruf Prozedur ist nicht wichtig, und die Datensatznummer des Parameters wird ignoriert.  
  
 Der Unterschied zwischen unbenannte Parameter und benannte Parameter ist in der Beziehung zwischen der Datensatznummer, des Deskriptors und die Anzahl der Parameter in der Prozedur. Wenn unbenannte Parameter verwendet werden, die erste parametermarkierung den ersten Datensatz in der Parameterdeskriptor, bezieht sich auf die wiederum auf den ersten Parameter (in Reihenfolge der Erstellung) im Aufruf Prozedur verknüpft ist. Wenn benannte Parameter verwendet werden, wird die erste parametermarkierung bezieht sich immer noch auf den ersten Datensatz der Parameterdeskriptor, aber die Beziehung zwischen der Datensatznummer, des Deskriptors und die Anzahl der Parameter in der Prozedur ist nicht mehr vorhanden. Benannte Parameter verwenden Sie die Zuordnung der die Datensatznummer Deskriptor nicht an die Prozedur Parameterposition. Stattdessen wird der Datensatz Deskriptorname die Namen der Prozedur Parameter zugeordnet.  
  
> [!NOTE]  
>  Wenn automatischer Auffüllung des IPD aktiviert ist, wird der Treiber den Deskriptor Auffüllen so, dass die Reihenfolge der deskriptordatensätze die Reihenfolge der Parameter in der Prozedurdefinition entspricht, selbst wenn benannte Parameter verwendet werden.  
  
 Wenn ein benannter Parameter verwendet wird, müssen alle Parameter Parameter benannt werden. Ist ein der Parameter kein benannter Parameter, werden klicken Sie dann keine von der Zertifizierungsstelle für die Parameter benannte Parameter. Wenn es eine Mischung aus benannten Parametern und unbenannte Parameter gäbe, wäre das Verhalten treiberabhängig.  
  
 Nehmen wir als Beispiel für benannte Parameter an eine SQL-Server, die gespeicherte Prozedur wie folgt definiert wurde:  
  
```  
CREATE PROCEDURE test @title_id int = 1, @quote char(30) AS <blah>  
```  
  
 In diesem Verfahren der erste Parameter, @title_id, hat den Standardwert 1. Eine Anwendung kann den folgenden Code verwenden, für das Aufrufen von dieser Prozedur so, dass nur ein dynamischen Parameter angegeben. Dieser Parameter ist ein benannter Parameter, mit dem Namen "\@Anführungszeichen".  
  
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
