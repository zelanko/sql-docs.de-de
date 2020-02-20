---
title: Vorlagenparameter ersetzen
ms.custom: seo-lt-2019
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b0c4cc26fddff13e388b74593aa9d8f9331359f8
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75245678"
---
# <a name="replace-template-parameters"></a>Vorlagenparameter ersetzen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
[Template Explorer](../../ssms/template/template-explorer.md)  
[Öffnen einer Vorlage](../../ssms/template/open-a-template.md)  
  
