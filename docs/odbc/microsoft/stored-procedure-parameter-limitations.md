---
title: Einschränkungen für Parameter der gespeicherten Prozedur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 8b804bcf-4cce-4e6f-aa45-00bab9ef9921
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 36f1c5a18eb9f0b1939a2c3602f1ebe7695741f7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948826"
---
# <a name="stored-procedure-parameter-limitations"></a>Parametereinschränkungen von gespeicherten Prozeduren
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Wenn Sie gespeicherte Oracle-Prozeduren ausführen, die 10 oder mehr Ausgabeparameter verwenden, tritt beim Aufrufen der gespeicherten Prozedur ein Fehler auf, was zu einer Zugriffsverletzung oder einem ActiveX Data Objects (ADO) führt. Dies kann bei Verwendung des Microsoft ODBC-Treibers für Oracle mit den Versionen 8.0.4.0.0 und 8.0.4.0.4 der Oracle-Client Software auftreten.  
  
 Um das Problem zu beheben, muss die Oracle-Client Software auf Version 8.0.4.2.0 oder höher aktualisiert werden. Weitere Informationen zu den [Patches](../../odbc/microsoft/oracle-software-patches.md)erhalten Sie von der Oracle Corporation.  
  
> [!NOTE]  
>  Dieses Problem tritt nicht bei der frühen Veröffentlichung der Oracle-Client Softwareversion 8.0.3.0.0 auf.
