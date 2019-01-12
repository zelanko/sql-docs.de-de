---
title: SQL Server-Replikation ' Publisher' (Dialogfeld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publishersettings.f1
helpviewer_keywords:
- Publisher Settings dialog box
ms.assetid: 4fb70427-082d-4179-82a1-34b235accc43
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1f1100f1c19a658fa6fe4b90816dca948e640a76
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54135640"
---
# <a name="sql-server-replication-publisher-settings-dialog-box"></a>SQL Server-Replikation ' Publisher' (Dialogfeld)
  Im Dialogfeld **Verlegereinstellungen** können Sie die Einstellungen für Verleger ändern, die dem linken Bereich des Replikationsmonitors hinzugefügt wurden.  
  
## <a name="options"></a>Optionen  
 **Verlegerverbindung**  
 Klicken Sie auf diese Option, um das Dialogfeld **Verbindung mit dem Server herstellen** zu starten. In diesem Dialogfeld können Sie die Verbindungseigenschaften und Anmeldeinformationen anzeigen und ändern, die vom Replikationsmonitor für die Verbindung mit einem Verleger verwendet werden.  
  
 **Verteilerverbindung**  
 Wird nur angezeigt, wenn vom Verleger ein Remoteverteiler verwendet wird. Klicken Sie auf diese Option, um das Dialogfeld **Verbindung mit dem Server herstellen** zu starten. In diesem Dialogfeld können Sie die Verbindungseigenschaften und Anmeldeinformationen anzeigen und ändern, die vom Replikationsmonitor für die Verbindung mit dem Remoteverteiler verwendet werden.  
  
 **Beim Starten des Replikationsmonitors automatisch Verbindung herstellen**  
 Wählen Sie diese Option aus, damit der Replikationsmonitor automatisch eine Verbindung mit dem Verteiler herstellt und Statusinformationen für den Verleger abruft, der im Raster im oberen Bereich des Dialogfelds ausgewählt ist. Wenn dieses Kontrollkästchen deaktiviert ist, müssen Sie nach dem Starten des Replikationsmonitors manuell eine Verbindung herstellen: Klicken Sie dazu mit der rechten Maustaste auf den Verleger im linken Bereich des Replikationsmonitors, und klicken Sie dann auf **Verbinden**.  
  
 **Status dieses Verlegers und seiner Veröffentlichungen automatisch aktualisieren**  
 Wählen Sie diese Option aus, damit der Replikationsmonitor automatisch den Status für den Verleger aktualisiert, der im Raster im oberen Bereich des Dialogfelds ausgewählt ist. Wenn diese Option ausgewählt ist, ruft der Replikationsmonitor die Statusinformationen für den Verleger und seine Veröffentlichungen über den Verteiler ab. Das Abrufintervall wird durch die Option **Aktualisierungsrate** festgelegt. Weitere Informationen zum Aktualisieren im Replikationsmonitor finden Sie unter [Zwischenspeichern, Aktualisieren und Leistung des Replikationsmonitors](monitor/caching-refresh-and-replication-monitor-performance.md).  
  
 **Aktualisierungsrate**  
 Geben Sie einen Wert (in Sekunden) ein, um anzugeben, wie oft der Replikationsmonitor Statusinformationen über den Verteiler abrufen soll. Geringere Werte führen zu einem häufigeren Abruf, was die Leistung des Verteilers beeinträchtigen kann, wenn eine große Anzahl von Verlegern überwacht wird. Es wird empfohlen, das eigene System zu testen, um einen angemessenen Wert zu bestimmen. Die Einstellung **Aktualisierungsrate** wird ebenfalls verwendet, wenn Sie in einem der Detailfenster des Replikationsmonitors die Option **Automatisch aktualisieren** ausgewählt haben.  
  
 **Diese(n) Verleger in der folgenden Gruppe anzeigen**  
 Wählen Sie eine Verlegergruppe aus der Liste aus. Der Verleger wird unter dieser Gruppe im linken Bereich angezeigt. Gruppen stellen eine Möglichkeit zum Organisieren von Verlegern dar und haben keinen Einfluss auf die Funktion der Replikation.  
  
 **Neue Gruppe**  
 Klicken Sie auf diese Option, um eine neue Verlegergruppe zu erstellen. Eine Verlegergruppe stellt eine einfache Möglichkeit dar, um die Verleger innerhalb des Replikationsmonitors zu organisieren. Gruppen haben keinen Einfluss auf die Replikation der Daten oder die Beziehungen zwischen den Servern in der Replikationstopologie.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten des Replikationsmonitors](monitor/start-the-replication-monitor.md)   
 [Überwachen der Replikation](monitoring-replication.md)  
  
  
