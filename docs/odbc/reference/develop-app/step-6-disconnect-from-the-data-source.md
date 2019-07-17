---
title: 'Schritt 6: Aus der Datenquelle zu trennen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], disconnecting from data source
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
ms.assetid: 6ad759ba-4721-4d8f-9b26-de976d4fc1a0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 65cc2ae8d2c2248a733e6efa9537fd3b40bb8fd1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114124"
---
# <a name="step-6-disconnect-from-the-data-source"></a>Schritt 6: Trennen der Verbindung mit der Datenquelle
Der letzte Schritt besteht aus der Datenquelle zu trennen, wie in der folgenden Abbildung dargestellt. Die Anwendung zunächst durch Aufrufen von alle Anweisungshandles freigibt **SQLFreeHandle**. Weitere Informationen finden Sie unter [Freigeben einer Anweisungshandle](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 ![Zeigt die aus einer Datenquelle trennen](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 Als Nächstes die Datenquelle mit die Anwendung trennt **SQLDisconnect** und das Verbindungshandle mit freigegeben **SQLFreeHandle**. Weitere Informationen finden Sie unter [Trennen von einer Datenquelle oder Treiber](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
 Schließlich gibt die Anwendung frei, das Umgebungshandle mit **SQLFreeHandle** und entlädt den Treiber-Manager. Weitere Informationen finden Sie unter [zuordnen, die Umgebung behandeln](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).
