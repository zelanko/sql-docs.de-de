---
description: Fehlerbehandlung in ADO
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 092f1a767e614b3426db63c95ca8bf4e14954dd0
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806870"
---
# <a name="error-handling-in-ado"></a>Fehlerbehandlung in ADO
ADO verwendet mehrere verschiedene Methoden, um eine Anwendung über Fehler zu benachrichtigen, die auftreten. In diesem Abschnitt werden die Fehlertypen erläutert, die auftreten können, wenn Sie ADO verwenden und wie Ihre Anwendung benachrichtigt wird. Abschließend werden Vorschläge zur Behandlung dieser Fehler angezeigt.  
  
## <a name="how-does-ado-report-errors"></a>Wie meldet ADO Fehler?  
 ADO benachrichtigt Sie über Fehler auf verschiedene Weise:  
  
-   ADO-Fehler generieren einen Laufzeitfehler. Behandeln Sie einen ADO-Fehler auf dieselbe Weise wie andere Laufzeitfehler, wie z. b. die Verwendung einer **On Error** -Anweisung in Visual Basic.  
  
-   Das Programm kann Fehler von OLE DB empfangen. Ein OLE DB Fehler generiert auch einen Laufzeitfehler.  
  
-   Wenn der Fehler für den Datenanbieter spezifisch ist, werden mindestens ein **Fehler** Objekt in die **Fehler** Auflistung des **Verbindungs** Objekts eingefügt, das beim Auftreten des Fehlers für den Zugriff auf den Datenspeicher verwendet wurde.  
  
-   Wenn der Prozess, der ein Ereignis ausgelöst hat, ebenfalls zu einem Fehler geführt hat, werden Fehlerinformationen in einem **Fehler** Objekt abgelegt und als Parameter an das Ereignis übergeben. Weitere Informationen zu Ereignissen finden Sie unter [Behandeln von ADO-Ereignissen](./handling-ado-events.md) .  
  
-   Probleme, die bei der Verarbeitung von Batch Aktualisierungen oder anderen Massen Vorgängen im Zusammenhang mit einem **Recordset** auftreten, können durch die **Status** -Eigenschaft des **Recordsets**angegeben werden. Beispielsweise können Schema Einschränkungs Verletzungen oder unzureichende Berechtigungen durch **recordstatuusenum** -Werte angegeben werden.  
  
-   Probleme, die im Zusammenhang mit einem bestimmten **Feld** im aktuellen Datensatz auftreten, werden auch von der **Status** -Eigenschaft jedes **Felds** in der **Fields** -Auflistung des **Datensatzes** oder **Recordsets**angezeigt. Beispielsweise können Updates, die nicht abgeschlossen werden konnten, oder nicht kompatible Datentypen von **fieldstatus usenum** -Werten angegeben werden.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [ADO-Fehler](./ado-errors.md)  
  
-   [Anbieterfehler](./provider-errors.md)  
  
-   [Fehlerinformationen im Zusammenhang mit Feldern](./field-related-error-information.md)  
  
-   [Fehlerinformationen in Bezug auf Recordsets](./recordset-related-error-information.md)  
  
-   [Behandeln von Fehlern in anderen Sprachen](./handling-errors-in-other-languages.md)  
  
-   [Vorhersehen von Fehlern](./anticipating-errors.md)