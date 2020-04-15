---
title: Verbindungsgriffe | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d5b03e0733e35984350d2a218b885dc148ca8f8f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299020"
---
# <a name="connection-handles"></a>Verbindungshandles
Eine *Verbindung* besteht aus einem Treiber und einer Datenquelle. Ein Verbindungshandle identifiziert jede Verbindung. Das Verbindungshandle definiert nicht nur, welchen Treiber verwendet werden soll, sondern auch welche Datenquelle mit diesem Treiber verwendet werden soll. Innerhalb eines Codesegments, das ODBC implementiert (treiber-Manager oder Treiber), identifiziert das Verbindungshandle eine Struktur, die Verbindungsinformationen enthält, z. B. die folgenden:  
  
-   Der Zustand der Verbindung  
  
-   Die aktuelle Diagnose auf Verbindungsebene  
  
-   Die Handles von Anweisungen und Deskriptoren, die derzeit für die Verbindung zugewiesen sind  
  
-   Die aktuellen Einstellungen der einzelnen Verbindungsattribute  
  
 ODBC verhindert mehrere gleichzeitige Verbindungen nicht, wenn der Treiber sie unterstützt. Daher können in einer bestimmten ODBC-Umgebung mehrere Verbindungshandles auf eine Vielzahl von Treibern und Datenquellen, auf denselben Treiber und eine Vielzahl von Datenquellen oder sogar auf mehrere Verbindungen mit demselben Treiber und derselben Datenquelle verweisen. Einige Treiber begrenzen die Anzahl der aktiven Verbindungen, die sie unterstützen. Die Option SQL_MAX_DRIVER_CONNECTIONS in **SQLGetInfo** gibt an, wie viele aktive Verbindungen ein bestimmter Treiber unterstützt.  
  
 Verbindungshandles werden hauptsächlich verwendet, wenn eine Verbindung mit der Datenquelle (**SQLConnect**, **SQLDriverConnect**oder **SQLBrowseConnect**) hergestellt wird, die Verbindung von der Datenquelle (**SQLDisconnect )** getrennt wird, Informationen über den Treiber und die Datenquelle (**SQLGetInfo**) abgerufen werden, Diagnosen abrufen (**SQLGetDiagField** und **SQLGetDiagRec**) und Transaktionen ausführen (**SQLEndTran**). Sie werden auch beim Festlegen und Abrufen von Verbindungsattributen (**SQLSetConnectAttr** und **SQLGetConnectAttr**) und beim Abrufen des systemeigenen Formats einer**SQL-Anweisung ( SQLNativeSql**) verwendet.  
  
 Verbindungshandles werden mit **SQLAllocHandle** zugewiesen und mit **SQLFreeHandle**freigegeben.
