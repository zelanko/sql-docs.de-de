---
title: Festlegen von Warnungsschwellenwerten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.setwarningthreshold.f1
ms.assetid: 17f93147-e7d9-4092-b4c2-c11b38051171
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9f1c7c05a02c67fda968ea26bd114d16b0b73925
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65805160"
---
# <a name="set-warning-thresholds"></a>Schwellenwerte für Warnung festlegen
  Mithilfe dieses Dialogfelds können Sie einen oder mehrere Warnungsschwellenwerte für die in der Navigationsstruktur des Dialogfelds **Datenbankspiegelungs-Monitor** ausgewählte Datenbank aktivieren und konfigurieren.  
  
 Mit dem Dialogfeld wird versucht, eine Verbindung mit beiden Serverinstanzen herzustellen. Diese Verbindungen werden asynchron hergestellt. Das Dialogfeld zeigt den Verbindungsstatus von jedem Partner an. Wenn der Partner nicht verbunden ist, können Sie auf **Verbinden**klicken.  
  
 **So verwenden Sie SQL Server Management Studio zum Überwachen der Daten Bank Spiegelung**  
  
-   [Starten des Datenbankspiegelungs-Monitors &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a>Tastatur  
 *Server Instanz und zugehörige Verbindungsstatus*  
 Der Name einer Partner Serverinstanz in der Form _System_**\\**_instance_name_. Für eine Standardserverinstanz wird nur der Systemname angezeigt.  
  
 Dieses Feld zeigt auch an, ob der Monitor zum aktuellen Zeitpunkt mit der Serverinstanz verbunden ist. Folgende Werte sind für den Verbindungsstatus möglich:  
  
-   **Nicht verbunden mit**  *server_instance_name*  
  
-   Es wird **versucht, eine Verbindung zu***server_instance_name*    
  
-   **Verbunden mit**  *server_instance_name*  
  
    > [!NOTE]  
    >  Wenn Sie kein Mitglied der festen Serverrolle **sysadmin** sind, lautet dieser Statuts **Verbunden mit** *Name der Serverinstanz* **(Begrenzte Berechtigungen)**.  
  
 Der Name jeder der Partnerserverinstanzen wird in einem separaten Feld für die *Serverinstanz und den zugehörigen Verbindungsstatus* angezeigt. Das oberste Feld listet den Prinzipalserver auf, wenn die Ausführung des Monitors gestartet wurde.  
  
 **Verbindung**/**Abbrechen**  
 Eine Schaltfläche " **Connect**/**Abbrechen** " ist jeder *Server Instanz und den zugehörigen Verbindungsstatus* Feldern zugeordnet. Der Status der Schaltfläche ist abhängig vom Verbindungsstatus:  
  
-   Wenn keine Verbindung mit der Serverinstanz besteht, lautet der Schaltflächentext **Verbinden**. Klicken Sie auf die Schaltfläche, um eine Verbindung mit der Serverinstanz herzustellen.  
  
-   Wenn gerade ein Verbindungsversuch ausgeführt wird, lautet der Schaltflächentext **Abbrechen**. Klicken Sie auf die Schaltfläche, um den Verbindungsversuch abzubrechen.  
  
-   Wenn der Server verbunden ist, lautet der Schaltflächentext **Verbunden**, und die Schaltfläche ist abgeblendet.  
  
 **Schutz**  
 Das Raster **Schwellenwerte** zeigt die Warnungseinstellungen für beide Serverinstanzen an.  
  
> [!NOTE]  
>  Wenn eine Serverinstanz nicht verbunden ist, werden die Spalten mit leeren Zellen und grauem Hintergrund angezeigt. Wenn die Verbindung geöffnet wird, zeigt das Raster automatisch den Inhalt der Instanz an.  
  
 Das Raster enthält die folgenden Spalten:  
  
 **Warnungen**  
 Listet die unterstützten Warnungen auf:  
  
|Warnung|BESCHREIBUNG|  
|-------------|-----------------|  
|**Warnen, wenn das nicht gesendete Protokoll den Schwellenwert überschreitet**|Der Schwellenwert gibt die Anzahl der Kilobytes (KB) des nicht gesendeten Protokolls in der Sendewarteschlange auf dem Prinzipal an.|  
|**Warnen, wenn das nicht wiederhergestellte Protokoll den Schwellenwert überschreitet**|Der Schwellenwert gibt die Anzahl an KB der Wiederholungswarteschlange auf der Spiegelserverinstanz an.|  
|**Warnen, wenn das Alter der ältesten, nicht gesendeten Transaktion den Schwellenwert überschreitet**|Der Schwellenwert gibt die Anzahl der Transaktionsminuten an, die noch nicht aus der Sendewarteschlange an die Spiegelserverinstanz gesendet wurden. Dieser Wert hilft, das Datenverlustrisiko in Bezug auf die Zeit zu messen.|  
|**Warnen, wenn der Spiegelungscommitaufwand den Schwellenwert überschreitet**|Der Schwellenwert gibt die Anzahl der Verzögerung pro Transaktion in Millisekunden an. Dieser Wert ist nur im Modus für hohe Sicherheit relevant. Hierbei handelt es sich um die Verzögerung, die entsteht, während die Prinzipalserverinstanz darauf wartet, dass die Spiegelserverinstanz den Transaktionsprotokolldatensatz in die Wiederholungswarteschlange schreibt.|  
  
 **Aktiviert auf '** * \<Serverinstanz>* **'**  
 Ein leeres Kontrollkästchen gibt an, dass die Warnung zum jetzigen Zeitpunkt auf der Serverinstanz deaktiviert ist. Klicken Sie auf das zugehörige Kontrollkästchen, um eine Warnung zu aktivieren.  
  
 **Schwellenwert auf '** * \<Serverinstanz>* **'**  
 Legen Sie den Schwellenwert auf der linken Seite der Spalte fest, wenn eine Warnung aktiviert ist. Ein Ereignis tritt beim Erreichen des angegebenen Schwellenwerts auf, wenn die Statustabelle aktualisiert wird. Wenn Sie einen Schwellenwert nach dem Konfigurieren eines Werts deaktivieren, verbleibt der betreffende Wert in diesem Feld und wird verwendet, sobald Sie die Warnung wieder aktivieren.  
  
 Wenn eine Warnung nicht aktiviert ist, ist dieses Feld inaktiv.  
  
 **OK**  
 Wenn Sie auf **OK** klicken, wird das Dialogfeld geschlossen, und die aktuell angegebenen Warnungsschwellenwerte werden im Raster **Schwellenwerte** auf der Seite **Warnungen**angezeigt.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Schwellenwert gilt jeweils nur auf einem Partner. Es ist jedoch empfehlenswert, einen Schwellenwert für ein bestimmtes Ereignis auf beiden Partnern festzulegen, um sicherzustellen, dass die Warnung weiterhin angezeigt wird, wenn ein Failover der Datenbank erfolgt. Der geeignete Schwellenwert für jeden Partner ist abhängig von der Leistungsfähigkeit des Systems des betreffenden Partners.  
  
 Ein Ereignis wird nur dann in das Ereignisprotokoll für eine Leistung geschrieben, sofern der Wert seinen Schwellenwert erreicht oder überschreitet, wenn die Statustabelle aktualisiert wird. Wenn ein Spitzenwert den Schwellenwert vorübergehend zwischen zwei Statusupdates erreicht, wird dieser Spitzenwert nicht erkannt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten des Datenbankspiegelungs-Monitors &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Überwachen der Daten Bank Spiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Starten des Assistenten zum Konfigurieren der Sicherheit für die Datenbankspiegelung &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
