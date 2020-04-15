---
title: Thread-Support (Visual FoxPro ODBC-Treiber) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303081"
---
# <a name="thread-support-visual-foxpro-odbc-driver"></a>Threadunterstützung (Visual FoxPro-ODBC-Treiber)
Der Visual FoxPro ODBC-Treiber ist threadsicher. Der Zugriff auf Umgebungshandles (*hen*), Verbindungshandles (*hdbc*) und Anweisungshandles (*hstmt*) ist in entsprechende Semaphore eingeschlossen, um zu verhindern, dass andere Prozesse auf die internen Datenstrukturen des Treibers zugreifen und möglicherweise die internen Datenstrukturen des Treibers ändern.  
  
 In einer Multithreadanwendung können Sie eine Funktion, die synchron auf einem *hstmt* ausgeführt wird, abbrechen, indem Sie [SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md) in einem separaten Thread aufrufen.  
  
 Der Treiber verwendet einen separaten Thread, um Daten abzurufen, wenn Sie progressives Abrufen verwenden. Um progressives Abrufen für eine Datenquelle zu verwenden, aktivieren Sie das Kontrollkästchen **Daten im Hintergrund** abrufen im [Dialogfeld ODBC Visual FoxPro Setup,](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) oder verwenden Sie das Schlüsselwort BackgroundFetch-Attribut in ihrer Verbindungszeichenfolge. Vermeiden Sie die Verwendung des Hintergrundabrufs, wenn Sie den Treiber aus Multithreadanwendungen aufrufen. Informationen zu Schlüsselwörtern für Verbindungszeichenfolgen-Attributfindenfinden finden Sie unter [Verwenden von Verbindungszeichenfolgen](../../odbc/microsoft/using-connection-strings.md).  
  
 Weitere Informationen zu Threads und **SQLCancel**finden Sie unter [SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md) in der *ODBC-Programmiererreferenz*.
