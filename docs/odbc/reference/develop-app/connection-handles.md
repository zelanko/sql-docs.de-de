---
title: Verbindungshandles | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection handles [ODBC]
- handles [ODBC], connection
ms.assetid: 12222653-f04d-46d6-bdee-61348f5d550f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77fdb63f346ada40346544a53c3ff69db0a8a9a4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63280851"
---
# <a name="connection-handles"></a>Verbindungshandles
Ein *Verbindung* besteht aus einem Treiber und einer Datenquelle. Ein Verbindungshandle identifiziert jede Verbindung. Das Verbindungshandle definiert, nicht nur den zu verwendenden Treiber, sondern welche Datenquelle Sie mit diesen Treiber verwenden. In einem Segment des Codes, die ODBC (des Treiber-Managers oder eines Treibers) implementiert, identifiziert das Verbindungshandle für eine Struktur, die Verbindungsinformationen, z. B. Folgendes enthält:  
  
-   Der Status der Verbindung  
  
-   Die aktuellen Verbindungsebene-Diagnose  
  
-   Die Ziehpunkte der Anweisungen und Deskriptoren für die Verbindung derzeit belegt.  
  
-   Die aktuellen Einstellungen der einzelnen Attribute für die Verbindung  
  
 ODBC verhindert nicht mehrere gleichzeitige Verbindungen, wenn der Treiber unterstützt. Aus diesem Grund können in einer bestimmten ODBC-Umgebung mehrere Verbindungshandles eine Vielzahl von Treibern und Datenquellen, denselben Treiber und eine Vielzahl von Datenquellen oder sogar mehrere Verbindungen, die denselben Treiber und die Datenquellensicht zeigen. Einige Treiber beschränken die Anzahl der aktiven Verbindungen, die sie unterstützen. die SQL_MAX_DRIVER_CONNECTIONS option **SQLGetInfo** gibt an, wie viele aktive Verbindungen, die ein bestimmter Treiber unterstützt.  
  
 Verbindungshandles dienen in erster Linie beim Verbinden mit der Datenquelle (**SQLConnect**, **SQLDriverConnect**, oder **SQLBrowseConnect**), die aus den Daten trennen Quelle (**SQLDisconnect**), Abrufen von Informationen über die Treiber und die Datenquelle (**SQLGetInfo**), Abrufen von Diagnose (**SQLGetDiagField** und **SQLGetDiagRec**), und die Durchführung von Transaktionen (**SQLEndTran**). Sie werden auch verwendet, wenn festlegen und Abrufen von Verbindungsattributen (**SQLSetConnectAttr** und **SQLGetConnectAttr**) und beim Abrufen von im systemeigenen Format von einer SQL-Anweisung (**SQLNativeSql** ).  
  
 Verbindungshandles zugeordnet sind **SQLAllocHandle** und mit freigegebenen **SQLFreeHandle**.
