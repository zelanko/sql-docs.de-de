---
title: SQL-Module | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 351d1c6a34413b385bd76dfebb009b34c4c0f150
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280424"
---
# <a name="sql-modules"></a>SQL-Module
Die zweite Technik zum Senden von SQL-Anweisungen an das DBMS erfolgt über Module. Kurz gesagt, ein Modul besteht aus einer Gruppe von Prozeduren, die aus der Host-Programmiersprache aufgerufen werden. Jede Prozedur enthält eine einzelne SQL-Anweisung, und Daten werden über Parameter an und von der Prozedur übergeben.  
  
 Ein Modul kann als Objektbibliothek betrachtet werden, die mit dem Anwendungscode verknüpft ist. Wie genau die Verfahren und der Rest der Anwendung miteinander verknüpft sind, hängt jedoch von der Implementierung ab. Die Prozeduren können z. B. in Objektcode kompiliert und direkt mit dem Anwendungscode verknüpft werden, sie können kompiliert und auf dem DBMS gespeichert werden und Aufrufe von Zugriffsplanbezeichnern, die im Anwendungscode platziert sind, oder sie können zur Laufzeit interpretiert werden.  
  
 Der Hauptvorteil von Modulen besteht darin, dass sie SQL-Anweisungen sauber von der Programmiersprache trennen. Theoretisch sollte es möglich sein, das eine zu ändern, ohne das andere zu ändern und sie einfach neu zu verknüpfen.
