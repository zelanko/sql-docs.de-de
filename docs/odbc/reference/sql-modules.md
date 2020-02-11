---
title: SQL-Module | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL modules [ODBC]
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], modules
- modules [ODBC]
- SQL statements [ODBC], modules
ms.assetid: 07551472-87ee-4765-951f-1364ed32f0c0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1b5cef56cec30e5ad09500135e05884bf55d5dde
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076224"
---
# <a name="sql-modules"></a>SQL-Module
Die zweite Methode zum Senden von SQL-Anweisungen an das DBMS ist die Verwendung von Modulen. Kurz gesagt besteht ein Modul aus einer Gruppe von Prozeduren, die von der Host Programmiersprache aufgerufen werden. Jede Prozedur enthält eine einzelne SQL-Anweisung, und die Daten werden über Parameter an und aus der Prozedur übermittelt.  
  
 Ein Modul kann als Objektbibliothek betrachtet werden, die mit dem Anwendungscode verknüpft ist. Die Art und Weise, in der die Prozeduren und der Rest der Anwendung verknüpft sind, ist jedoch implementierungsabhängig. Die Prozeduren können z. b. in den Objektcode kompiliert und direkt mit dem Anwendungscode verknüpft werden. Sie können auf dem DBMS kompiliert und gespeichert werden, und es können Aufrufe von Zugriffs Plan Bezeichner erfolgen, die im Anwendungscode abgelegt werden, oder Sie können zur Laufzeit interpretiert werden.  
  
 Der Hauptvorteil von Modulen besteht darin, dass Sie SQL-Anweisungen ordnungsgemäß von der Programmiersprache trennen. Theoretisch sollte es möglich sein, eine Änderung zu ändern, ohne die andere zu ändern und Sie einfach neu zu verknüpfen.
