---
description: Microsoft Cursor-Dienst für OLE DB
title: Der Microsoft-Cursor Dienst für OLE DB | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: f3646ec86f76fcba2f6b82759a4784de7d463279
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452742"
---
# <a name="the-microsoft-cursor-service-for-ole-db"></a>Microsoft Cursor-Dienst für OLE DB
Wenn Sie einen Client seitigen Cursor auswählen oder die **CursorLocation** -Eigenschaft auf **adUseClient**festlegen, rufen Sie den Microsoft-Cursor Dienst für OLE DB auf. Möglicherweise werden auch Verweise auf das "Clientcursormodul" angezeigt, das im Zusammenhang mit ADO identisch ist. Dieser Dienst ergänzt die Cursor Unterstützungsfunktionen von Datenanbietern. Daher können Sie eine relativ einheitliche Funktionalität von allen Datenanbietern wahrnehmen.  
  
 Der Cursor Dienst für OLE DB stellt dynamische Eigenschaften zur Verfügung und verbessert das Verhalten bestimmter Methoden. Die Eigenschaft dynamische **Optimierung** ermöglicht beispielsweise das Erstellen temporärer Indizes, um bestimmte Vorgänge, wie z. b. die **Find** -Methode, zu vereinfachen.  
  
 Der Cursor Dienst ermöglicht die Unterstützung für Batch Aktualisierungen in allen Fällen. Außerdem simuliert Sie mehr fähige Cursor Typen, z. b. dynamische Cursor, wenn ein Datenanbieter nur weniger fähige Cursor bereitstellen kann, z. b. statische Cursor.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft-Cursor Dienst für OLE DB (ADO-Dienst Komponente)](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)
