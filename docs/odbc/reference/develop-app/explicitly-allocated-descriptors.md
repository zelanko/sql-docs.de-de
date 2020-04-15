---
title: Explizit zugewiesene Deskriptoren | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305691"
---
# <a name="explicitly-allocated-descriptors"></a>Explizit zugewiesene Deskriptoren
Eine Anwendung kann eine Anwendungsbeschreibung für eine Verbindung explizit zuweisen, wenn sie mit der Datenbank verbunden ist. Durch Die Angabe dieses Deskriptorhandles als Attribut eines Anweisungshandles mithilfe von **SQLSetStmtAttr**weist die Anwendung den Treiber an, diesen Deskriptor anstelle der entsprechenden implizit zugewiesenen Anwendungsdeskriptoren zu verwenden. Die Anwendung kann keine alternativen Implementierungsdeskriptoren angeben.  
  
 Eine Anwendung kann einen explizit zugewiesenen Deskriptor mehreren Anweisungsausweisen zuordnen. Nur wenn eine Anwendung tatsächlich mit der Datenbank verbunden ist, kann ein Deskriptor ein explizit zugewiesener Deskriptor sein. Die Anwendung kann einen solchen Deskriptor explizit oder implizit befreien, indem sie ihre Verbindung freigibt.
