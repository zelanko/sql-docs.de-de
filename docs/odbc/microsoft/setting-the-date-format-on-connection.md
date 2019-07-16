---
title: Festlegen des Datumsformats für Verbindung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date formats [ODBC]
- ODBC driver for Oracle [ODBC], date formats
ms.assetid: ba0d5123-db52-448b-8e19-b7647ce4b361
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3075893d37a401110afbecacc68e452425ad684b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063466"
---
# <a name="setting-the-date-format-on-connection"></a>Festlegen des Datumsformats für eine Verbindung
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Die neue Version des Microsoft ODBC-Treibers für Oracle wird nicht automatisch das Datumsformat für Oracle-Datumsfelder festgelegt werden. Wenn der Treiber verbunden, es bislang `ALTER SESSION SET NLS_DATE_FORMAT ='YYYY-MM-DD HH:MI:SS'`.  
  
 Um das Datum das Format festzulegen, rufen Sie die Gruppe für ALTER-SITZUNG, und führen Sie die Einfügung. Zum Beispiel:  
  
```  
conn.Execute "ALTER SESSION SET NLS_DATE_FORMAT = 'YYYY-MM-DD HH:MI:SS' "  
sSql = "INSERT INTO DATETEST VALUES (24,'1988-12-01 10:23:03')"  
conn.Execute sSql  
```
