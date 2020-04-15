---
title: SQLRowCount (Cursorbibliothek) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLRowCount function [ODBC], Cursor Library
ms.assetid: 781cf5a5-325e-4523-8633-d96d9e98277c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf9fe597f54ecb4bc82439251e2228ac5fdc4ea3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300590"
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLRowCount-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen **zu SQLRowCount**finden Sie unter [SQLRowCount Function](../../../odbc/reference/syntax/sqlrowcount-function.md).  
  
 Wenn eine Anwendung **SQLRowCount** mit der dem Cursor zugeordneten Anweisung aufruft, gibt die Cursorbibliothek die Anzahl der Datenzeilen zurück, die sie vom Treiber abgerufen hat.  
  
 Wenn eine Anwendung **SQLRowCount** mit der Anweisung aufruft, die einer positionierten Aktualisierungs- oder Löschanweisung zugeordnet ist, gibt die Cursorbibliothek die Anzahl der Zeilen zurück, die von der Anweisung betroffen sind.  
  
 Wenn eine Anwendung **SQLRowCount** nach einer **SELECT-Anweisung** aufruft, gibt die Cursorbibliothek -1 zurück.
