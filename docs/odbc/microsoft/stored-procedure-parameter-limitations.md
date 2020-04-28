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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbd748884575791d5f170e95bc5aa465b61624b7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299200"
---
# <a name="stored-procedure-parameter-limitations"></a>Parametereinschränkungen von gespeicherten Prozeduren
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Wenn Sie gespeicherte Oracle-Prozeduren ausführen, die 10 oder mehr Ausgabeparameter verwenden, tritt beim Aufrufen der gespeicherten Prozedur ein Fehler auf, was zu einer Zugriffsverletzung oder einem ActiveX Data Objects (ADO) führt. Dies kann bei Verwendung des Microsoft ODBC-Treibers für Oracle mit den Versionen 8.0.4.0.0 und 8.0.4.0.4 der Oracle-Client Software auftreten.  
  
 Um das Problem zu beheben, muss die Oracle-Client Software auf Version 8.0.4.2.0 oder höher aktualisiert werden. Weitere Informationen zu den [Patches](../../odbc/microsoft/oracle-software-patches.md)erhalten Sie von der Oracle Corporation.  
  
> [!NOTE]  
>  Dieses Problem tritt nicht bei der frühen Veröffentlichung der Oracle-Client Softwareversion 8.0.3.0.0 auf.
