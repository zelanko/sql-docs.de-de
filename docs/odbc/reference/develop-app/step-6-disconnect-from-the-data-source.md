---
title: 'Schritt 6: Trennen sie von der Datenquelle | Microsoft Docs'
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
ms.openlocfilehash: df8cd94435d74bf813b0b64be0753a0beb44d354
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302791"
---
# <a name="step-6-disconnect-from-the-data-source"></a>Schritt 6: Trennen der Verbindung mit der Datenquelle
Der letzte Schritt besteht darin, die Verbindung zur Datenquelle zu trennen, wie in der folgenden Abbildung dargestellt. Zuerst gibt die Anwendung alle Anweisungshandles frei, indem **SIE SQLFreeHandle aufruft.** Weitere Informationen finden Sie unter [Befreien eines Anweisungshandles](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 ![Zeigt das Trennen einer Verbindung zu einer Datenquelle](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 Als Nächstes trennt die Anwendung die Verbindung zur Datenquelle mit **SQLDisconnect** und gibt das Verbindungshandle mit **SQLFreeHandle**frei. Weitere Informationen finden Sie unter [Trennen von einer Datenquelle oder einem Treiber](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
 Schließlich gibt die Anwendung den Umgebungshandle mit **SQLFreeHandle** frei und entlädt den Treiber-Manager. Weitere Informationen finden Sie unter [Zuweisen des Umgebungshandles](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).
