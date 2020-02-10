---
title: Editor für den Task ' Prozess ausführen ' (Seite verarbeiten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executeprocesstask.process.f1
helpviewer_keywords:
- Execute Process Task Editor
ms.assetid: 0fc22406-e79b-47a4-a7e4-108d4ce6202f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fa799404777f8f0ef0a8a07a81c8c7961c636004
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66059031"
---
# <a name="execute-process-task-editor-process-page"></a>Editor für den Task 'Prozess ausführen' (Seite Verarbeiten)
  Auf der Seite **Verarbeiten** des Dialogfelds **Editor für den Task 'Prozess ausführen'** können Sie die Optionen konfigurieren, die den Prozess ausführen. Zu den Optionen gehören der Name der ausführbaren Datei, der Speicherort dieser Datei, die Argumente der Eingabeaufforderung und die Variablen für die Ein- und Ausgabe.  
  
 Informationen, um sich mit diesem Thema vertraut zu machen, finden Sie unter [Execute Process Task](control-flow/execute-process-task.md).  
  
## <a name="options"></a>Tastatur  
 **Requirements fullfilename**  
 Geben Sie an, ob der Task fehlschlagen soll, wenn die ausführbare Datei am angegebenen Speicherort nicht gefunden wird.  
  
 **Bares**  
 Geben Sie den Namen der ausführbaren Datei ein.  
  
 **Argumente**  
 Geben Sie Argumente für die Eingabeaufforderung an.  
  
 **WorkingDirectory**  
 Geben Sie den Pfad zu dem Ordner ein, in dem die ausführbare Datei enthalten ist, oder klicken Sie auf die Schaltfläche zum Durchsuchen **(...)**, und suchen Sie den Ordner.  
  
 **Standard Input Variable**  
 Wählen Sie eine Variable für die Bereitstellung der Eingabe zum Prozess aus, oder klicken Sie auf \<**Neue Variable...**>, um eine neue Variable zu erstellen:  
  
 **Verwandte Themen:**  [Variable hinzufügen](../../2014/integration-services/add-variable.md)  
  
 **StandardOutputVariable**  
 Wählen Sie eine Variable für die Erfassung der Prozessausgabe aus, oder klicken Sie auf \<**Neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **StandardErrorVariable**  
 Wählen Sie eine Variable für die Erfassung der Fehlerausgabe des Prozesses aus, oder klicken Sie auf \<**Neue Variable...**>, um eine neue Variable zu erstellen.  
  
 **Failtaskifreturncodeisnotsuccess Value**  
 Geben Sie an, ob beim Task ein Fehler auftritt, wenn der Prozessexitcode von dem unter **SuccessValue**angegebenen Wert abweicht.  
  
 **SuccessValue**  
 Geben Sie den Wert an, der von der ausführbaren Datei zurückgegeben wird, um einen Erfolg zu melden. Standardmäßig ist dieser Wert auf **0**festgelegt.  
  
 **Zeit**  
 Geben Sie die Anzahl von Sekunden an, die der Prozess ausgeführt werden kann. Durch den Wert **0** wird angezeigt, dass kein Timeoutwert verwendet wird und der Prozess so lange ausgeführt wird, bis er entweder abgeschlossen ist oder ein Fehler auftritt.  
  
 **Terminateprocessaftertimeout**  
 Geben Sie an, ob das Ende des Prozesses nach Ablauf des durch die Option **TimeOut** angegebenen Timeoutzeitraumes erzwungen wird. Diese Option ist nur verfügbar, wenn der Wert unter **TimeOut** nicht **0**ist.  
  
 **WindowStyle**  
 Geben Sie die Fensteranordnung an, in der der Prozess ausgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)  
  
  
