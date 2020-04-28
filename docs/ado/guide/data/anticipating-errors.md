---
title: Antizipieren von Fehlern | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925983"
---
# <a name="anticipating-errors"></a>Vorhersehen von Fehlern
Die Fehler Verhinderung ist mindestens so wichtig wie die Fehlerbehandlung. Dieser letzte Abschnitt enthält eine kurze Liste der Vorsichtsmaßnahmen, die Ihre Anwendung ausführen kann, um die Wahrscheinlichkeit von Fehlern zu verringern.  
  
 Überprüfen Sie den Zustand von Objekten, indem Sie den Wert in der **State** -Eigenschaft überprüfen, bevor Sie versuchen, einen Vorgang mit diesen Objekten auszuführen. Wenn Ihre Anwendung z. b. eine globale **Verbindung**verwendet, überprüfen Sie die **Status** -Eigenschaft, um festzustellen, ob Sie bereits geöffnet ist, bevor Sie die **Open** -Methode aufrufen.  
  
-   Jedes Programm, das Daten von einem Benutzer akzeptiert, muss Code enthalten, um diese Daten vor dem Senden an den Datenspeicher zu überprüfen. Sie können sich nicht auf den Datenspeicher, den Anbieter, ADO oder sogar Ihre Programmiersprache verlassen, um Sie über Probleme zu informieren. Sie müssen jedes Byte überprüfen, das von Ihren Benutzern eingegeben wurde, und sicherstellen, dass die Daten der richtige Typ für das Feld sind und dass erforderliche Felder nicht leer sind.  
  
 Überprüfen Sie die Daten, bevor Sie versuchen, Daten in den Datenspeicher zu schreiben. Die einfachste Möglichkeit hierfür ist, das **WillMove** -Ereignis oder das **willupdaterecordset** -Ereignis zu behandeln. Eine ausführlichere Erläuterung der Behandlung von ADO-Ereignissen finden Sie unter [Behandeln von ADO](../../../ado/guide/data/handling-ado-events.md)-Ereignissen.  
  
 Stellen Sie sicher, dass **Recordset** -Objekte nicht die Grenzen des **Recordsets** überschreiten, bevor Sie versuchen, den Daten Satz Zeiger zu verschieben. **Wenn Sie** versuchen, die Datei " **EOF** " auf "true" oder " **muveprev** **" zu verwenden** , tritt ein Fehler auf. Wenn Sie **eine der Verschiebungs Methoden ausführen** , wenn sowohl **EOF** als auch **BOF** true sind, wird ein Fehler generiert.  
  
 Fehler treten **auch auf,** Wenn Sie versuchen, Vorgänge auszuführen, z. b. suchen und nach einem leeren **Recordset** **Suchen** .
