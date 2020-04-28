---
title: Thread Unterstützung (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- thread support [ODBC]
- Visual FoxPro ODBC driver [ODBC], thread support
- FoxPro ODBC driver [ODBC], thread support
- multithreaded applications [ODBC]
ms.assetid: 0c6abbbc-012b-41aa-bded-5e7e362d015b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2aa19eb233525b5a65ef67fe9903814fc1163177
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303081"
---
# <a name="thread-support-visual-foxpro-odbc-driver"></a>Threadunterstützung (Visual FoxPro-ODBC-Treiber)
Der Visual FoxPro-ODBC-Treiber ist Thread sicher. Der Zugriff auf Umgebungs Handles (*Henne*), Verbindungs Handles (*hdbc*) und Anweisungs Handles (*hstmt*) ist in entsprechende Semaphoren integriert, um zu verhindern, dass andere Prozesse auf die internen Datenstrukturen des Treibers zugreifen und diese potenziell ändern können.  
  
 In einer Multithreadanwendung können Sie eine Funktion, die synchron ausgeführt wird, auf einem *hstmt* durch Aufrufen von [SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md) in einem separaten Thread abbrechen.  
  
 Der Treiber verwendet einen separaten Thread zum Abrufen von Daten, wenn Sie progressives abrufen verwenden. Wenn Sie progressives abrufen für eine Datenquelle verwenden möchten, aktivieren Sie das Kontrollkästchen **Daten im Hintergrund abrufen** im [Dialogfeld Visual FoxPro-Setup von ODBC](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) , oder verwenden Sie das backgroundfetch-Attribut Schlüsselwort in der Verbindungs Zeichenfolge. Vermeiden Sie die Verwendung von Hintergrund Abruf, wenn Sie den Treiber aus Multithreadanwendungen abrufen. Weitere Informationen zu Schlüsselwörtern für Verbindungs Zeichenfolgen-Attribute finden [Sie unter Using Connection Strings](../../odbc/microsoft/using-connection-strings.md).  
  
 Weitere Informationen zu Threads und **SQLCancel**finden Sie unter [SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md) in der *ODBC Programmer es Reference*.
