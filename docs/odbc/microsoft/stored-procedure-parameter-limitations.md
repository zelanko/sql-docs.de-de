---
title: Einschränkungen der gespeicherten Prozedurparameter | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299200"
---
# <a name="stored-procedure-parameter-limitations"></a>Parametereinschränkungen von gespeicherten Prozeduren
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Wenn Sie gespeicherte Oracle-Prozeduren ausführen, die 10 oder mehr Ausgabeparameter verwenden, schlägt der Aufruf der gespeicherten Prozedur fehl, was zu einem Access Violation- oder ActiveX Data Objects (ADO)-Fehler führt. Dies kann auftreten, wenn der Microsoft ODBC-Treiber für Oracle mit den Versionen 8.0.4.0.0 und 8.0.4.0.4 der Oracle-Clientsoftware verwendet wird.  
  
 Um das Problem zu beheben, muss die Oracle-Clientsoftware auf Version 8.0.4.2.0 oder höher aktualisiert werden. Wenden Sie sich an Oracle Corporation, um weitere Informationen zu den Patches zu [erhalten.](../../odbc/microsoft/oracle-software-patches.md)  
  
> [!NOTE]  
>  Dieses Problem tritt nicht bei der frühen Veröffentlichung der Oracle-Clientsoftware Version 8.0.3.0.0 auf.
