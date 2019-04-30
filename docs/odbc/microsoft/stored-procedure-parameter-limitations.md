---
title: Gespeicherte Prozedur Parametereinschränkungen | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 7dc74811bf6cead91850ebd3fcaa8cf64025c80d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63270857"
---
# <a name="stored-procedure-parameter-limitations"></a>Parametereinschränkungen von gespeicherten Prozeduren
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Bei der Ausführung von Oracle, gespeicherte Prozeduren, die Nutzung von 10 oder mehr Ausgabeparameter, schlägt der Aufruf der gespeicherten Prozedur fehl, eine Zugriffsverletzung oder ActiveX Data Objects (ADO) Fehlermeldung angezeigt. Dies kann auftreten, wenn der Microsoft ODBC-Treiber für Oracle mit den Versionen 8.0.4.0.0 und 8.0.4.0.4 der Oracle-Clientsoftware.  
  
 Um das Problem zu beheben, muss die Oracle-Clientsoftware ein Upgrade auf Version 8.0.4.2.0 oder höher sein. Wenden Sie sich an Oracle Corporation für Weitere Informationen zu den [Patches](../../odbc/microsoft/oracle-software-patches.md).  
  
> [!NOTE]  
>  Dieses Problem tritt nicht mit der frühen Veröffentlichung von Oracle-Clientsoftwareversion 8.0.3.0.0.
