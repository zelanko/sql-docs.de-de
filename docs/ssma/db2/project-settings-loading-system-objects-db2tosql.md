---
title: Projekteinstellungen (Laden von System Objekten) (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9a545233-1b0a-488a-a1ec-c33aa608dcc1
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 5c12a2ddb97c6d599e5adfc57277e0a5f64288e5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68060192"
---
# <a name="project-settingsloading-system-objects-db2tosql"></a>Projekteinstellungen (Laden von System Objekten) (DB2ToSQL)
Auf der Seite System Objekte Laden des Dialog Felds **Projekteinstellungen** können Sie angeben, welche DB2-System Objekte von SSMA konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]und in geladen werden.  
  
Der Bereich System Objekte laden ist in den Dialogfeldern **Projekteinstellungen** und **Standard Projekteinstellungen** verfügbar:  
  
-   Wenn Sie Einstellungen für alle SSMA-Projekte angeben möchten, wählen Sie **im Menü Extras** die Option **Standard Projekteinstellungen**aus, wählen Sie den Migrations Projekttyp aus, für den die Einstellungen in der Dropdown Liste **Migrations Ziel Version** angezeigt oder geändert werden müssen, klicken Sie unten im linken Bereich auf **Allgemein** , und klicken Sie dann auf **System Objekte laden**.  
  
-   Um Einstellungen für das aktuelle Projekt anzugeben, wählen Sie **im Menü Extras** die **Option Projekteinstellungen**aus, klicken Sie unten im linken Bereich auf **Allgemein** , und klicken Sie dann auf **System Objekte laden**.  
  
## <a name="default-settings"></a>Standardeinstellungen  
Die Umstellung von System Objekten beansprucht Systemressourcen und nimmt Zeit in Anspruch. Um die Leistung zu verbessern, wählt SSMA nur die am häufigsten verwendeten Systemobjekte aus, wie in der folgenden Liste gezeigt:  
  
-   Einsetzt. DBMS_OUTPUT  
  
-   Einsetzt. DBMS_PIPE  
  
-   Einsetzt. DBMS_UTILITY  
  
-   Einsetzt. Norm  
  
-   Einsetzt. UTL_FILE  
  
-   Einsetzt. DBMS_LOB  
  
-   Einsetzt. DBMS_SQL  
  
-   Einsetzt. DBMS_SESSION  
  
Wenn die DB2-Objekte auf zusätzliche Systemobjekte verweisen, sollten Sie diese Objekte auswählen. Wenn Sie die Systemobjekte, auf die von den DB2-Datenbankobjekten verwiesen wird, nicht auswählen, meldet SSMA Konvertierungs Fehler. Wenn Sie Konvertierungs Fehler erhalten, die durch fehlende Systemobjekte verursacht wurden, wählen Sie die fehlenden Objekte in diesem Dialogfeld aus. Anschließend können Sie die Konvertierung bei Bedarf wiederholen.  
  
