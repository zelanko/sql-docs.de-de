---
description: Vorlagenparameter ersetzen
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
ms.openlocfilehash: 5daa809acf191527b72a6ea65b666b396dd51b68
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468522"
---
# <a name="replace-template-parameters"></a>Vorlagenparameter ersetzen
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
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
  
