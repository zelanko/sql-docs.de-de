---
title: Ersetzen von Vorlagenparametern|Microsoft-Dokumente
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.templates.replaceparameters.f1
helpviewer_keywords:
- template parameters [Template Explorer]
- templates [Transact-SQL], replacing parameters
- Replace (Query) Template Parameters dialog box
- replacing template parameters
ms.assetid: 1234aa14-3464-4a3e-922a-5cfb8fb23627
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 620569275c85bc12f678f64c927956d57452792f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47722499"
---
# <a name="replace-template-parameters"></a>Vorlagenparameter ersetzen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Vorlagen enthalten Parameter, die bei jeder Verwendung der betreffenden Vorlage durch implementierungsspezifische Werte ersetzt werden können. Nach dem Öffnen einer Vorlage in einem Code-Editor können Sie die Parameter durch für die Implementierung relevante Werte ersetzen.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
Das Dialogfeld **Werte für Vorlagenparameter angeben** ist ein Raster mit drei Spalten. Die Spalten **Parameter** und **Typ** sind schreibgeschützt und können nicht geändert werden. Überprüfen Sie den Inhalt der Spalte **Wert** , und ändern Sie die Standardwerte in für die Implementierung geeignete Werte.  
  
Um das Dialogfeld verwenden zu können, müssen die im Skript enthaltenen Parameter in spitze Klammern (`< >`) gesetzt und in folgendem Format angegeben werden: `<`*Parametername*`,` *Datentyp*`,` *Standardwert*`>`.  
  
## <a name="replace-template-parameters"></a>Vorlagenparameter ersetzen  
Nach dem Öffnen der Vorlage in einem Code-Editor-Fenster:  
  
1.  Klicken Sie im Menü **Abfrage** auf **Werte für Vorlagenparameter angeben**.  
  
2.  Im Dialogfeld **Werte für Vorlagenparameter angeben** enthält die Spalte **Werte** jeweils einen vorgeschlagenen Wert für jeden Parameter. Akzeptieren Sie den Wert, oder ersetzen Sie ihn durch einen neuen Wert.  
  
3.  Klicken Sie auf **OK** , um das Dialogfeld **Vorlagenparameter ersetzen** zu schließen und das Skript im Abfrage-Editor zu ändern.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Template Explorer](../../ssms/template/template-explorer.md)  
[Öffnen einer Vorlage](../../ssms/template/open-a-template.md)  
  
