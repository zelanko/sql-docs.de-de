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
manager: craigg
ms.openlocfilehash: 30c116878049c4f6a8f36e988731ab641e03c6d7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47834748"
---
# <a name="sql-modules"></a>SQL-Module
Das zweite Verfahren für das Senden von SQL-Anweisungen für das DBMS ist über Module. Kurz gesagt, besteht aus einem Modul eine Gruppe von Prozeduren, die von der Programmiersprache Host aufgerufen werden. Jede Prozedur eine einzelne SQL­Anweisung enthält, und Daten werden in und aus der Prozedur über Parameter übergeben.  
  
 Ein Modul kann als eine Objektbibliothek betrachtet werden, die auf den Anwendungscode verknüpft ist. Ist abhängig von der Implementierung jedoch genau wie die Prozeduren und die übrigen Teile der Anwendung verknüpft sind. Z. B. die Prozeduren in Objektcode kompiliert und direkt mit Code der Anwendung verknüpft werden können, kompiliert und gespeichert, auf dem DBMS und Aufrufe auf Plan-IDs, die im Anwendungscode platziert werden konnte oder sie zur Laufzeit interpretiert werden konnte.  
  
 Der Hauptvorteil von Modulen ist, dass sie ordnungsgemäß SQL-Anweisungen von der Programmiersprache trennen. In der Theorie sollte es möglich, einer ohne die andere geändert, und verknüpfen Sie sie einfach erneut.
