---
title: Fehlerbehandlung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- reporting errors [ADO]
- errors [ADO]
- ADO, error handling
ms.assetid: 4909e413-f3b0-4183-8ad3-67b1434df742
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 56d41b8c8fddff4d49cdb213834f45eac7fd5462
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700756"
---
# <a name="error-handling"></a>Fehlerbehandlung
ADO verwendet verschiedene Methoden, um eine Anwendung der Fehler zu benachrichtigen, die auftreten. Dieser Abschnitt beschreibt die Arten von Fehlern, die auftreten können, bei Verwendung von ADO und wie Ihre Anwendung benachrichtigt wird. Es schließt seine Untersuchung mit Empfehlungen dazu, wie Sie diesen Fehler zu behandeln.  
  
## <a name="how-does-ado-report-errors"></a>Wie meldet ADO Fehler?  
 ADO informiert Sie über Fehler auf verschiedene Weise:  
  
-   ADO-Fehler generieren einen Laufzeitfehler. Behandeln Sie einen ADO-Fehler gleichen genauso wie jeder andere Fehler in einem Laufzeitfehler, z. B. die Verwendung einer **On Error** -Anweisung in Visual Basic.  
  
-   Das Programm kann Fehler von OLE DB empfangen. Ein OLE DB-Fehler generiert ebenfalls ein Laufzeitfehler ausgegeben.  
  
-   Wenn der Fehler auf Ihren Datenanbieter, einen oder mehrere bestimmte **Fehler** Objekte befinden sich der **Fehler** Auflistung von der **Verbindung** -Objekt, das verwendet wurde, für den Datenzugriff Speichern Sie, wenn der Fehler aufgetreten ist.  
  
-   Wenn der Prozess, der ein Ereignis ausgelöst, auch einen Fehler erzeugt, befindet sich Fehlerinformationen einer **Fehler** -Objekt und das Ereignis als Parameter übergeben. Finden Sie unter [Handling ADO Events](../../../ado/guide/data/handling-ado-events.md) für Weitere Informationen zu Ereignissen.  
  
-   Probleme, die auftreten, bei der Verarbeitung von batch-Updates anderer Vorgänge oder Massenvorgänge im Zusammenhang mit einer **Recordset** kann angegeben werden. durch die **Status** Eigenschaft der **Recordset**. Z. B. einschränkungsverletzungen Schema oder keine ausreichenden Berechtigungen können angegeben werden durch **RecordStatusEnum** Werte.  
  
-   Im Zusammenhang mit einem bestimmten auftretende Probleme **Feld** im aktuellen Datensatz werden auch angezeigt, durch die **Status** Eigenschaft der einzelnen **Feld** in die **Felder**  Auflistung von der **Datensatz** oder **Recordset**. Z. B. Updates, die nicht abgeschlossen werden konnte oder nicht kompatiblen Datentypen können angegeben werden durch **FieldStatusEnum** Werte.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [ADO-Fehler](../../../ado/guide/data/ado-errors.md)  
  
-   [Anbieterfehler](../../../ado/guide/data/provider-errors.md)  
  
-   [Fehlerinformationen im Zusammenhang mit Feldern](../../../ado/guide/data/field-related-error-information.md)  
  
-   [Recordset-bezogene Fehlerinformationen](../../../ado/guide/data/recordset-related-error-information.md)  
  
-   [Behandeln von Fehlern in anderen Sprachen](../../../ado/guide/data/handling-errors-in-other-languages.md)  
  
-   [Vorhersehen von Fehlern](../../../ado/guide/data/anticipating-errors.md)
