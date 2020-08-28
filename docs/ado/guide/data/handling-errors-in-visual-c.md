---
description: Behandeln von Fehlern in Visual C++
title: Behandeln von Fehlern in Visual C++ | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- errors [ADO], Visual C++
- Visual C++ error handling [ADO]
ms.assetid: b7576f07-020a-45f7-9e79-b5756f33f7ab
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f61f6b9f27011543545932f9ce7d9e5d434bbf9
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980621"
---
# <a name="handling-errors-in-visual-c"></a>Behandeln von Fehlern in Visual C++
In com geben die meisten Vorgänge einen HRESULT-Rückgabecode zurück, der angibt, ob eine Funktion erfolgreich abgeschlossen wurde. Die #Import-Direktive generiert Wrapper Code um jede "RAW"-Methode oder-Eigenschaft und überprüft das zurückgegebene HRESULT. Wenn HRESULT einen Fehler anzeigt, löst der Wrapper Code einen com-Fehler aus, indem _com_issue_errorex () mit dem HRESULT-Rückgabecode als Argument aufgerufen wird. COM-Fehler Objekte können in einem **try-catch-** Block abgefangen werden. (Aus Effizienzgründen sollten Sie einen Verweis auf ein _com_error Objekt abfangen.)  
  
 Beachten Sie, dass es sich hierbei um ADO-Fehler handelt: Sie ergeben einen Fehler beim ADO-Vorgang. Fehler, die vom zugrunde liegenden Anbieter zurückgegeben werden, werden in der **Fehler** Auflistung des **Verbindungs** Objekts als **Fehler** Objekte angezeigt.  
  
 Die #Import-Direktive erstellt nur Fehlerbehandlungsroutinen für Methoden und Eigenschaften, die in der ADO. dll deklariert werden. Allerdings können Sie denselben Mechanismus zur Fehlerbehandlung nutzen, indem Sie ein eigenes Fehler Überprüfungs Makro oder eine Inline Funktion schreiben. Beispiele finden Sie im Thema Visual C++®-Erweiterungen.
