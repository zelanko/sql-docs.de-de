---
description: Daten-Viewer
title: Daten-Viewer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.dataviewer.f1
helpviewer_keywords:
- Data Viewer dialog box
ms.assetid: 6351309a-688f-4e82-9697-1712130f10a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8e3f659ec65cece6dd36f4fc0bc09ecae70a46c3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430942"
---
# <a name="data-viewer"></a>Daten-Viewer

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Wenn ein Pfad zu einem Daten-Viewer konfiguriert ist, zeigt dieser Daten-Viewer die Daten pufferweise an, während sie zwischen zwei Datenflusskomponenten fließen.  
  
## <a name="options"></a>Optionen  
 **Grüner Pfeil**  
 Klicken Sie auf den Pfeil, um die Daten des nächsten Puffers anzuzeigen. Wenn die Daten in einem einzigen Puffer verschoben werden können, ist diese Option nicht verfügbar.  
  
 **Trennen**  
 Trennt den Daten-Viewer.  
  
 **Hinweis** Durch das Trennen des Daten-Viewers wird dieser nicht gelöscht. Wenn der Daten-Viewer getrennt wurde, fließen die Daten weiterhin durch den Pfad, aber der Daten-Viewer wird nicht mehr aktualisiert, um die Daten in den einzelnen Puffern anzuzeigen.  
  
 **Anfügen**  
 Fügt einen Daten-Viewer an.  
  
 **Hinweis** Wenn der Daten-Viewer angefügt wird, zeigt er die Informationen der einzelnen Puffer des Datenflusses an und hält dann an. Mithilfe des grünen Pfeils können Sie durch die einzelnen Puffer klicken.  
  
 **Daten kopieren**  
 Kopiert die Daten des aktuellen Puffers in die Zwischenablage.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen des Datenflusses](../../integration-services/troubleshooting/debugging-data-flow.md)  
  
  
