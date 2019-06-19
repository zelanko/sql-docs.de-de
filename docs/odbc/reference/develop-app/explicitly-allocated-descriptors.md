---
title: Explizit reserviert Deskriptoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- explicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: f590251d-56a6-4d58-a405-9e85e68fbc47
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fbec69e0d984d843abc2b8754e111a1199c79a5a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63049789"
---
# <a name="explicitly-allocated-descriptors"></a>Explizit zugewiesene Deskriptoren
Eine Anwendung kann explizit einen Anwendungsdienst-Deskriptor für eine Verbindung zu einem beliebigen Zeitpunkt zuordnen, die sie mit der Datenbank verbunden ist. Durch diese Deskriptorhandles angeben, wie ein Attribut einer Anweisung mit **SQLSetStmtAttr**, die Anwendung leitet den Treiber mit dieser Deskriptor anstelle der entsprechenden implizit zugeordnete Anwendung Deskriptoren. Die Anwendung kann nicht auf alternative Implementierung Deskriptoren angeben.  
  
 Eine Anwendung kann mehr als eine Anweisung einen explizit zugewiesenen Deskriptor zuordnen. Nur, wenn eine Anwendung tatsächlich mit der Datenbank verbunden ist kann ein Deskriptor einen explizit zugewiesenen-Deskriptor sein. Die Anwendung kann solche einen Deskriptor explizit oder implizit freigeben, indem Sie seine Verbindung freigeben sein zu müssen.
