---
title: Abrufen von Datentyp Informationen mit SQLGetTypeInfo | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL data types [ODBC], identifiers
- SQLGetTypeInfo function [ODBC], retrieving data type information
- retrieving data type information [ODBC]
- type identifiers [ODBC], SQL
- identifiers [ODBC], SQL type
- SQL type identifiers [ODBC]
ms.assetid: d4f8b152-ab9e-4d05-a720-d10a08a6df81
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ec2bbba824eaf3d74133cf9754eca2593c9fb79
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300060"
---
# <a name="retrieving-data-type-information-with-sqlgettypeinfo"></a>Abrufen von Datentypinformationen mit SQLGetTypeInfo
Da die Zuordnungen von zugrunde liegenden SQL-Datentypen zu ODBC-Typbezeichnern ungefähr zueinander stehen, bietet ODBC eine Funktion (**SQLGetTypeInfo**), über die ein Treiber jeden SQL-Datentyp in der Datenquelle vollständig beschreiben kann. Diese Funktion gibt ein Resultset zurück, in dem jede Zeile die Merkmale eines einzelnen Datentyps beschreibt, z. b. Name, Typbezeichner, Genauigkeit, Skalierung und NULL-Zulässigkeit.  
  
 Diese Informationen werden in der Regel von generischen Anwendungen verwendet, die es dem Benutzer ermöglichen, Tabellen zu erstellen und zu ändern. Solche Anwendungen rufen **SQLGetTypeInfo** auf, um die Datentyp Informationen abzurufen, und stellen dann einige oder alle für den Benutzer dar. Solche Anwendungen müssen zwei Dinge beachten:  
  
-   Mehr als ein SQL-Datentyp kann einem einzelnen Typbezeichner zugeordnet werden, wodurch es schwierig werden kann, den zu verwendenden Datentyp zu ermitteln. Um dieses Problem zu beheben, wird das Resultset zuerst nach Typbezeichner und zweitens durch die Nähe der Definition des Typbezeichners geordnet. Außerdem haben Datenquellen definierte Datentypen Vorrang vor benutzerdefinierten Datentypen. Nehmen wir beispielsweise an, dass eine Datenquelle die Datentypen integer und Counter als identisch definiert, mit dem Unterschied, dass der Wert automatisch inkrementiert wird. Angenommen, der benutzerdefinierte Typ "wholerum" ist ein Synonym für "Integer". Jeder dieser Typen ist SQL_INTEGER zugeordnet. Im Resultset **SQLGetTypeInfo** wird Integer zuerst angezeigt, gefolgt von wholenum und then Counter. "Wholenum" wird nach "Integer" angezeigt, weil es Benutzer definiert ist, aber vor "Counter", da es genauer mit der Definition des SQL_INTEGER Typbezeichners übereinstimmt.  
  
-   ODBC definiert keine Datentyp Namen für die Verwendung in **CREATE TABLE** -und **ALTER TABLE** -Anweisungen. Stattdessen sollte die Anwendung den Namen verwenden, der in der TYPE_NAME-Spalte des Resultsets zurückgegeben wird, das von **SQLGetTypeInfo**zurückgegeben wurde. Der Grund hierfür ist, dass die meisten SQL-Daten in der DBMSs-Datei nicht sehr unterschiedlich sind. Anstatt die Treiber zu zwingen, SQL-Anweisungen zu analysieren und Standard Datentyp Namen durch DBMS-spezifische Datentyp Namen zu ersetzen, erfordert ODBC, dass Anwendungen die DBMS-spezifischen Namen an erster Stelle verwenden.  
  
 Beachten Sie, dass **SQLGetTypeInfo** nicht notwendigerweise alle Datentypen beschreibt, auf die eine Anwendung stoßen kann. Die Resultsets können insbesondere Datentypen enthalten, die nicht direkt von der Datenquelle unterstützt werden. Beispielsweise werden die Datentypen der Spalten in Resultsets, die von Katalog Funktionen zurückgegeben werden, von ODBC definiert, und diese Datentypen werden möglicherweise nicht von der Datenquelle unterstützt. Um die Merkmale der Datentypen in einem Resultset zu ermitteln, ruft eine Anwendung **SQLColAttribute**auf.
