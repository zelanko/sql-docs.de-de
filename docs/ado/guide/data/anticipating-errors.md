---
title: Vorhersehen von Fehlern | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- anticipating errors [ADO]
- errors [ADO], preventing
- preventing errors [ADO]
ms.assetid: ea1d4a97-58c3-476b-a496-cc80db2a90d5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2d92d96e3b8cdfea5cacea35d852e8859de65dbd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925983"
---
# <a name="anticipating-errors"></a>Vorhersehen von Fehlern
Fehler zur Verhinderung von ist mindestens ebenso wichtig wie die Fehlerbehandlung. In diesem letzten Abschnitt enthält eine kurze Liste mit Vorsichtsmaßnahmen, die Ihre Anwendung ausführen kann, um seltener auf Fehler zu machen.  
  
 Überprüfen des Status von Objekten durch Überprüfung des Werts der **Zustand** Eigenschaft, bevor Sie versuchen, einen Vorgang mit diese Objekte ausführen. Wenn Ihre Anwendung eine globale verwendet z. B. **Verbindung**, überprüfen die **Zustand** Eigenschaft, um festzustellen, ob es bereits vor dem Aufruf geöffnet ist der **öffnen** Methode.  
  
-   Jedes Programm, das Daten von einem Benutzer akzeptiert, muss Code, um die Daten zu überprüfen, vor dem Senden an den Datenspeicher enthalten. Sie können nicht auf Datenspeicher, den Anbieter, ADO oder auch Ihre bevorzugte Programmiersprache, die Sie über Probleme informieren verlassen. Sie müssen jedes Byte von den Benutzern, und stellen Sie sicher, dass Daten der richtige Typ für das Feld und erforderlichen Felder nicht leer sind eingegebene überprüfen.  
  
 Überprüfen Sie die Daten, bevor Sie versuchen, alle Daten in den Datenspeicher zu schreiben. Die einfachste Möglichkeit hierzu ist, behandelt der **WillMove** Ereignis oder die **WillUpdateRecordset** Ereignis. Eine umfassendere Erläuterung der ADO-Ereignisse behandeln, finden Sie unter [Handling ADO Events](../../../ado/guide/data/handling-ado-events.md).  
  
 Stellen Sie sicher, dass **Recordset** Objekte sind nicht über die Grenzen hinaus die **Recordset** vor dem Versuch, die Zeiger für den Datensatz zu verschieben. Wenn Sie versuchen, **MoveNext** beim **EOF** ist "true" oder **MovePrev** beim **BOF** ist "true", tritt ein Fehler auf. Wenn Sie Ausführen der **verschieben** Methoden bei der beide **EOF** und **BOF** sind "true", wird ein Fehler generiert.  
  
 Außerdem kommt es zu Fehlern, wenn Sie versuchen, die Vorgänge auszuführen, z. B. **Seek** und **finden** für eine leere **Recordset**.
