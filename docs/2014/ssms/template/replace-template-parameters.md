---
title: Ersetzen von Vorlagenparametern|Microsoft-Dokumente
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.templates.replaceparameters.f1
helpviewer_keywords:
- template parameters [Template Explorer]
- templates [Transact-SQL], replacing parameters
- Replace (Query) Template Parameters dialog box
- replacing template parameters
ms.assetid: 1234aa14-3464-4a3e-922a-5cfb8fb23627
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1d87b17a110efe118f7796487448e4d3bae30375
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061900"
---
# <a name="replace-template-parameters"></a>Vorlagenparameter ersetzen
  Vorlagen enthalten Parameter, die bei jeder Verwendung der betreffenden Vorlage durch implementierungsspezifische Werte ersetzt werden können. Nach dem Öffnen einer Vorlage in einem Code-Editor können Sie die Parameter durch für die Implementierung relevante Werte ersetzen.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Das Dialogfeld **Werte für Vorlagenparameter angeben** ist ein Raster mit drei Spalten. Die Spalten **Parameter** und **Typ** sind schreibgeschützt und können nicht geändert werden. Überprüfen Sie den Inhalt der Spalte **Wert** , und ändern Sie die Standardwerte in für die Implementierung geeignete Werte.  
  
 Damit Sie dieses Dialogfeld verwenden können, müssen Sie Parameter im folgenden Format in spitzen Klammern (`< >`) in das Skript einfügen: `<`*Parametername*`,` *Datentyp*`,` *Standardwert*`>`.  
  
## <a name="replace-template-parameters"></a>Vorlagenparameter ersetzen  
 Nach dem Öffnen der Vorlage in einem Code-Editor-Fenster:  
  
1.  Klicken Sie im Menü **Abfrage** auf **Werte für Vorlagenparameter angeben**.  
  
2.  Im Dialogfeld **Werte für Vorlagenparameter angeben** enthält die Spalte **Werte** jeweils einen vorgeschlagenen Wert für jeden Parameter. Akzeptieren Sie den Wert, oder ersetzen Sie ihn durch einen neuen Wert.  
  
3.  Klicken Sie auf **OK** , um das Dialogfeld **Vorlagenparameter ersetzen** zu schließen und das Skript im Abfrage-Editor zu ändern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorlagen-Explorer](template-explorer.md)   
 [Öffnen einer Vorlage](open-a-template.md)  
  
  
