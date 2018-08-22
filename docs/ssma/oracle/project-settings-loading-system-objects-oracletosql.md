---
title: Projekteinstellungen (Laden von Systemobjekten) (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9418cb34-d869-4d24-95b3-6cb9db949bb0
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: af52d18e2978f8645bce689481f68121a164c160
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "40395688"
---
# <a name="project-settingsloading-system-objects-oracletosql"></a>Projekteinstellungen (Laden von Systemobjekten) (OracleToSQL)
Die Seite Laden von Systemobjekten der **Projekteinstellungen** Dialogfeld ermöglicht die Angabe der Oracle-Systemobjekte SSMA konvertiert und lädt in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Der Laden von Systemobjekten Bereich finden Sie in der **Projekteinstellungen** und **Projekt Standardeinstellungen** Dialogfelder:  
  
-   Die Einstellungen für alle SSMA-Projekten auf die **Tools** , wählen Sie im Menü **Projekt Standardeinstellungen**, wählen Sie die Migration-Projekttyp, die für die Einstellungen erforderlich sind, um angezeigt oder geändert werden, von **Migration Zielversion** öffnen Sie auf die Dropdownliste **allgemeine** am unteren Rand der linken Bereich ein, und klicken Sie dann auf **Laden von Systemobjekten**.  
  
-   Die Einstellungen für das aktuelle Projekt, auf die **Tools** , wählen Sie im Menü **Projekteinstellungen**, klicken Sie auf **allgemeine** am unteren Rand im linken Bereich, und klicken Sie dann auf **Beim Laden von Systemobjekten**.  
  
## <a name="default-settings"></a>Standardeinstellungen  
Konvertieren von Systemobjekten belegt Systemressourcen und nimmt Zeit in Anspruch. Zur Verbesserung der Leistung, wählt der SSMA nur die am häufigsten verwendeten Systemobjekte, wie in der folgenden Liste gezeigt:  
  
-   SYS.DBMS_OUTPUT  
  
-   SYS.DBMS_PIPE  
  
-   SYS.DBMS_UTILITY  
  
-   SYS.STANDARD  
  
-   SYS.UTL_FILE  
  
-   SYS.DBMS_LOB  
  
-   SYS.DBMS_SQL  
  
-   SYS.DBMS_SESSION  
  
Die Oracle-Objekte auf Weitere Objekte zu verweisen, sollten Sie diese Objekte auswählen. Wenn Sie nicht die Systemobjekte auswählen, die von Ihren Oracle-Datenbank-Objekten verwiesen wird, meldet SSMA Fehler bei der Konvertierung. Wenn Sie durch fehlende Systemobjekte verursacht Fehler bei der Konvertierung erhalten, wählen Sie die fehlenden Objekte in diesem Dialogfeld. Sie können dann die Konvertierung nach Bedarf wiederholen.  
  
