---
description: 'Schritt 6: Trennen der Verbindung mit der Datenquelle'
title: 'Schritt 6: Trennen der Verbindung mit der Datenquelle | Microsoft-Dokumentation'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 06b3b50653578388ca3d4e20b598f63879f38e88
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461342"
---
# <a name="step-6-disconnect-from-the-data-source"></a>Schritt 6: Trennen der Verbindung mit der Datenquelle
Der letzte Schritt besteht darin, die Verbindung mit der Datenquelle zu trennen, wie in der folgenden Abbildung dargestellt. Zuerst gibt die Anwendung alle Anweisungs Handles durch Aufrufen von **SQLFreeHandle**frei. Weitere Informationen finden Sie unter [Freigeben eines Anweisungs Handles](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 ![Zeigt das Trennen einer Verbindung zu einer Datenquelle](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 Als nächstes trennt die Anwendung die Verbindung mit der Datenquelle mit **SQLDisconnect** und gibt das Verbindungs Handle mit **SQLFreeHandle**frei. Weitere Informationen finden Sie unter [Trennen der Verbindung mit einer Datenquelle oder einem Treiber](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
 Schließlich gibt die Anwendung das Umgebungs Handle mit **SQLFreeHandle** frei und entlädt den Treiber-Manager. Weitere Informationen finden Sie unter [Zuordnen des Umgebungs Handles](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).
