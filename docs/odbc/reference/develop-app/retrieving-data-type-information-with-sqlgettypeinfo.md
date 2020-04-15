---
title: Abrufen von Datentypinformationen mit SQLGetTypeInfo | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300060"
---
# <a name="retrieving-data-type-information-with-sqlgettypeinfo"></a>Abrufen von Datentypinformationen mit SQLGetTypeInfo
Da die Zuordnungen von zugrunde liegenden SQL-Datentypen zu ODBC-Typbezeichnern ungefähr sind, stellt ODBC eine Funktion (**SQLGetTypeInfo**) bereit, über die ein Treiber jeden SQL-Datentyp in der Datenquelle vollständig beschreiben kann. Diese Funktion gibt ein Resultset zurück, in dem jede Zeile die Merkmale eines einzelnen Datentyps beschreibt, z. B. Name, Typbezeichner, Genauigkeit, Skalierung und NULL-Fähigkeit.  
  
 Diese Informationen werden im Allgemeinen von generischen Anwendungen verwendet, die es dem Benutzer ermöglichen, Tabellen zu erstellen und zu ändern. Solche Anwendungen rufen **SQLGetTypeInfo** auf, um die Datentypinformationen abzurufen und dann einige oder alle davon dem Benutzer zu präsentieren. Solche Anwendungen müssen sich zweier Dinge bewusst sein:  
  
-   Mehr als ein SQL-Datentyp kann einem einzelnen Typbezeichner zugeordnet werden, was es schwierig machen kann, den zu verwendenden Datentyp zu bestimmen. Um dieses Problem zu lösen, wird das Resultset zuerst nach Typbezeichner und zweitens nach Nähe zur Definition des Typbezeichners sortiert. Darüber hinaus haben Datenquellendefinierte Datentypen Vorrang vor benutzerdefinierten Datentypen. Angenommen, eine Datenquelle definiert die Datentypen INTEGER und COUNTER als identisch, mit der Ausnahme, dass COUNTER automatisch inkrementiert wird. Angenommen, der benutzerdefinierte Typ WHOLENUM ist ein Synonym von INTEGER. Jeder dieser Typen wird SQL_INTEGER zugeordnet. Im **SQLGetTypeInfo-Resultset** wird INTEGER zuerst angezeigt, gefolgt von WHOLENUM und dann COUNTER. WHOLENUM wird nach INTEGER angezeigt, weil es benutzerdefinierte ist, aber vor COUNTER, weil es enger mit der Definition des typiden Typbezeichners SQL_INTEGER übereinstimmt.  
  
-   ODBC definiert keine Datentypnamen für die Verwendung in **CREATE TABLE-** und **ALTER TABLE-Anweisungen.** Stattdessen sollte die Anwendung den Namen verwenden, der in der Spalte TYPE_NAME des von **SQLGetTypeInfo**zurückgegebenen Resultsets zurückgegeben wird. Der Grund dafür ist, dass die meisten SQL-Dateien zwar nicht sehr unterschiedlich sind, die Namen des Datentyps jedoch sehr unterschiedlich sind. Anstatt Treiber dazu zu zwingen, SQL-Anweisungen zu analysieren und Standarddatentypnamen durch DBMS-spezifische Datentypnamen zu ersetzen, erfordert ODBC, dass Anwendungen die DBMS-spezifischen Namen verwenden.  
  
 Beachten Sie, dass **SQLGetTypeInfo** nicht notwendigerweise alle Datentypen beschreibt, auf die eine Anwendung stoßen kann. Insbesondere können Ergebnismengen Datentypen enthalten, die nicht direkt von der Datenquelle unterstützt werden. Beispielsweise werden die Datentypen der Spalten in Resultsets, die von Katalogfunktionen zurückgegeben werden, von ODBC definiert, und diese Datentypen werden möglicherweise von der Datenquelle nicht unterstützt. Um die Eigenschaften der Datentypen in einem Resultset zu bestimmen, ruft eine Anwendung **SQLColAttribute**auf.
