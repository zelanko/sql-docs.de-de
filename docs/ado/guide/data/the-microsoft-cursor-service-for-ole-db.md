---
title: Microsoft Cursor Service für OLE DB | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursor service for ole db [ADO]
- cursors [ADO], cursor service for OLE DB
ms.assetid: 1ac3bd9b-2d45-4cc8-88ec-bd8a218cfb49
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e85d6f482b9d206b2ec705a8d890a4e34e5f2252
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63142929"
---
# <a name="the-microsoft-cursor-service-for-ole-db"></a>Microsoft Cursor-Dienst für OLE DB
Wenn Sie einen clientseitigen Cursor auswählen, oder legen Sie die **CursorLocation** Eigenschaft **AdUseClient**, Sie der Microsoft Cursor Service für OLE DB aufrufen. Sehen Sie möglicherweise auch Verweise auf die "Client Cursor-Engine", handelt es sich im Prinzip das gleiche im Kontext des ADO. Dieser Dienst ergänzt die cursorunterstützung Funktionen von Datenanbietern. Daher können Sie die relativ einheitliche Funktionalität von allen Datenanbietern wahrnehmen.  
  
 Der Cursor Service für OLE DB stellt dynamische Eigenschaften zur Verfügung und verbessert das Verhalten bestimmter Methoden. Z. B. die **optimieren** dynamische Eigenschaft ermöglicht das Erstellen temporärer Indizes, um bestimmte Vorgänge, z. B. erleichtern die **finden** Methode.  
  
 Der Cursor-Dienst ermöglicht die Unterstützung für Batchaktualisierungen in allen Fällen. Es simuliert auch noch leistungsfähigere Cursortypen, z. B. dynamic-Cursor, wenn ein Datenanbieter nur weniger leistungsfähige Cursor, wie z. B. statische Cursor angeben kann.  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft Cursor Service für OLE DB (ADO-Dienstkomponente)](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)
