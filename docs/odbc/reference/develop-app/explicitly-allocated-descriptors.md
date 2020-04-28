---
title: Explizit zugewiesene Deskriptoren | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a9950bc23a1e75606316039e6c2d66f3dba59940
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305691"
---
# <a name="explicitly-allocated-descriptors"></a>Explizit zugewiesene Deskriptoren
Eine Anwendung kann einen Anwendungs Deskriptor für eine Verbindung jederzeit explizit zuordnen, wenn Sie mit der Datenbank verbunden ist. Durch die Angabe dieses Deskriptorhandles als Attribut eines Anweisungs Handles mithilfe von **SQLSetStmtAttr**weist die Anwendung den Treiber an, diesen Deskriptor anstelle der entsprechenden implizit zugeordneten Anwendungs Deskriptoren zu verwenden. Die Anwendung kann keine alternativen Implementierungs Deskriptoren angeben.  
  
 Eine Anwendung kann einen explizit zugeordneten Deskriptor mit mehr als einer Anweisung verknüpfen. Nur wenn eine Anwendung tatsächlich mit der Datenbank verbunden ist, kann es sich bei einem Deskriptor um einen explizit zugewiesenen Deskriptor handeln. Die Anwendung kann einen solchen Deskriptor explizit oder implizit durch Freigeben der Verbindung freigeben.
