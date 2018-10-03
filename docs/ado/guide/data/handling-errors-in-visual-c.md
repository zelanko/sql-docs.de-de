---
title: Behandeln von Fehlern in Visual C++ | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e33d28201e1a2e4f7df8ac330ac89b3f00194b14
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47630668"
---
# <a name="handling-errors-in-visual-c"></a>Behandeln von Fehlern in Visual C++
In COM geben die meisten Vorgänge einen HRESULT-Rückgabecode, der angibt, ob eine Funktion erfolgreich abgeschlossen. Die #import-Direktive Wrappercode, um jede "rohes" Methode oder Eigenschaft generiert und überprüft das zurückgegebene HRESULT. Wenn HRESULT Fehler weist darauf hin, löst der Code einen COM-Fehler vom aufrufenden _com_issue_errorex() mit dem HRESULT-Rückgabecode als Argument an. COM-Fehlerobjekte abgefangen werden können, einem **Try / Catch** Block. (Aus Gründen der Effizienz fangen Sie einen Verweis auf ein _com_error-Objekt).  
  
 Denken Sie daran, diese ADO-Fehler: sie auf die ADO-Vorgangsfehler zurückzuführen. Fehler, die vom zugrunde liegenden Anbieter zurückgegeben werden, als **Fehler** Objekte in der **Verbindung** des Objekts **Fehler** Auflistung.  
  
 Die #import-Anweisung erstellt nur Routinen zur Fehlerbehandlung für Methoden und Eigenschaften, die in der ADO-DLL-Datei deklariert. Allerdings können Sie der gleichen Fehlerbehandlungs-Mechanismus nutzen durch Ihre eigene Überprüfung auf Fehler durch Makro oder zur Inlinefunktion-Funktion schreiben. Finden Sie im Visual C++®-Erweiterungen für Beispiele.
