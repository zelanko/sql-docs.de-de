---
title: Projekteinstellungen (Laden von System Objekten) (oracleto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9418cb34-d869-4d24-95b3-6cb9db949bb0
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 93e008c9d7518e7e171e7548c7353e4f83ccb8a1
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87933221"
---
# <a name="project-settingsloading-system-objects-oracletosql"></a>Projekteinstellungen (Laden von Systemobjekten) (OracleToSQL)
Auf der Seite System Objekte Laden des Dialog Felds **Projekteinstellungen** können Sie angeben, welche Oracle-System Objekte von SSMA konvertiert und in geladen werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
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
  
Wenn die Oracle-Objekte auf zusätzliche Systemobjekte verweisen, sollten Sie diese Objekte auswählen. Wenn Sie die Systemobjekte, auf die von den Oracle-Datenbankobjekten verwiesen wird, nicht auswählen, meldet SSMA Konvertierungs Fehler. Wenn Sie Konvertierungs Fehler erhalten, die durch fehlende Systemobjekte verursacht wurden, wählen Sie die fehlenden Objekte in diesem Dialogfeld aus. Anschließend können Sie die Konvertierung bei Bedarf wiederholen.  
  
