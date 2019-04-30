---
title: Hardwareinstallation - Analytics Platform System | Microsoft-Dokumentation
description: Dieser Artikel beschreibt, wie Sie verschieben, entpacken und installieren Sie die Hardware für Ihre SQL Server-PDW-Appliance. In diesem Artikel dient nur zu Informationszwecken und soll Ihnen ein Verständnis des Prozesses. Ihr Gerät sollte ausgepackt, installiert werden, und überprüft, bevor sie über für Sie aktiviert ist. Kunden die Teilnahme ist erforderlich, damit Elemente wie z. B. Daten center Zugriff, Stromversorgung und Ethernet-Verbindungen.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 169b38a1228f909a79d7866eba20b85b4a56c30b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63157316"
---
# <a name="hardware-installation-for-analytics-platform-system-appliance"></a>Hardwareinstallation für Analytics Platform System appliance
Dieser Artikel beschreibt, wie Sie verschieben, entpacken und installieren Sie die Hardware für Ihre SQL Server-PDW-Appliance. In diesem Artikel dient nur zu Informationszwecken und soll Ihnen ein Verständnis des Prozesses. Ihr Gerät sollte ausgepackt, installiert werden, und überprüft, bevor sie über für Sie aktiviert ist. Kunden die Teilnahme ist erforderlich, damit Elemente wie z. B. Daten center Zugriff, Stromversorgung und Ethernet-Verbindungen.  
  
## <a name="BeforeMoving"></a>Bevor Sie alle Komponenten von der Ladestation verschieben  
Führen Sie die folgenden Aufgaben aus, verschieben, entpacken, oder Sie Komponenten Gerät Auspacken.  
  
|Aufgabe|Description|  
|--------|---------------|  
|Stellen Sie sicher, dass alle Komponenten angekommen sind|Verwenden Sie die Rechnung von Materialien (BOM), um sicherzustellen, dass alle Komponenten empfangen und auf ihre Paletten am empfangenden Dock für Ihr Rechenzentrum.|  
|Stellen Sie sicher, dass das Rechenzentrum alle Anforderungen für die Appliance erfüllt|Starten Sie diese Aufgabe durch Überprüfen der Hardwarespezifikationen und Verkabelung der Diagramme, die von Ihrem unabhängigen Hardwarehersteller bereitgestellt. Die nächsten Schritte finden Sie Einzelheiten zu Gestell Platz und verbindungsanforderungen an.|  
|Stellen Sie sicher, dass der Data Center richtigen Rackplatz hat|Stellen Sie sicher, dass das Rechenzentrum genügend Speicherplatz für alle von der Appliance Racks verfügt.<br /><br />Stellen Sie sicher, dass die Rackplatz leer und für die Appliance Racks den Empfang bereit ist.|  
|Stellen Sie sicher, dass das Rechenzentrum Konnektivitätsanforderungen erfüllt|Stellen Sie sicher, dass das Rechenzentrum in den Diagrammen Verkabelung die Verkabelung erfüllt.<br /><br />Stellen Sie sicher, dass es Platz für alle Kabel und Netzkabel geben wird, nachdem die applianceknoten installiert werden.|  
|Stellen Sie sicher, dass die Stockwerken zwischen dem Dock und Racks Gewichtung Anforderungen zu erfüllen|Stellen Sie sicher, dass alle Bodenbeläge zwischen Paletten und Racks die Gewichtung der Einheit von Knoten, vor allem in Rechenzentren mit ausgelösten Stockwerke unterstützen kann.<br /><br />Wenden Sie sich an Ihrem unabhängigen Hardwarehersteller Informationen auf der Gewichtung der einzelnen Komponenten.|  
|Sichern Sie das Rechenzentrum rack|Sichern Sie das Rechenzentrum Rack an Stelle mithilfe zusätzlichen Komponenten nach Bedarf für Ihre Datencenter-Speicherort, z. B. Erdbeben Schultergurte in geografischen Bereichen anfällig für Erdbeben.|  
|Vorbereiten Sie für die Unterstützung bei der Übertragung von Komponenten|Im Voraus bestimmen Sie, welche Unterstützung zu erhalten, Geräte und Tools, die Sie jede Komponente zu behandeln, sicher und ohne dort Schaden anrichten können müssen.|  
  
## <a name="Moving"></a>Verschieben Sie den Racks von der Ladestation ins Datenzentrum  
Jeder Palette enthält alle Komponenten für die ein Gerät Rack, einschließlich der Knoten, Kabel, Kabel usw. an.  
  
Verwenden Sie die folgende Checkliste, um jedes Rack Gerät aus der Palette an der Ladestation an ihrem Speicherort Rack im Datencenter zu verschieben. Verschieben Sie zunächst das Steuerelement Rack, und klicken Sie dann verschieben Sie das Gerät Daten Racks zu.  
  
> [!WARNING]  
> Diese Schritte genau wie beschrieben ausführen könnten Bestimmung Schäden, Schäden an Ihre SQL Server-PDW-Appliance oder anderen Problemen führen.  
>   
> Nie wurde versucht, heben oder eine Appliance-Knoten oder eine andere hohe Komponente ohne Unterstützung zu erhalten oder geeignete Ausrüstung zu verschieben. Wenden Sie sich an Ihrem unabhängigen Hardwarehersteller Informationen auf der Gewichtung der einzelnen Komponenten, damit Sie im Voraus bestimmen können, welche Unterstützung zu erhalten, Geräte und Tools, die Sie jede Komponente zu behandeln, sicher und ohne dort Schaden anrichten können müssen.  
  
|Aufgabe|Description|  
|--------|---------------|  
|Stellen Sie sicher, dass die Palette Ebene ist.|Bevor Sie beginnen, verschieben oder zu packen, achten Sie darauf, dass es auf der Ebene von Grund auf neu ist.|  
|Unbolt einen Knoten aus der Palette|Beginnen Sie am oberen Rand der Palette, unbolt den obersten Knoten aus der Palette.|  
|Verschieben Sie den Knoten, in eine Transportwagen oder Warenkorb, der die Gewichtung unterstützen kann|Verwenden Sie Rampen und Techniken für den richtigen anheben/verschieben, verschieben den Knoten, in eine Transportwagen oder Warenkorb, der die Gewichtung unterstützen kann.|  
|Den Knoten in das Rechenzentrum übertragen|Verwenden Sie ordnungsgemäße anheben/Verschieben von Techniken, um den Knoten an Position in der Datencenter-Racks zu verschieben.|  
|Sichern Sie den Knoten im Rechenzentrum rack|Sichern Sie den Knoten direkt in das Rechenzentrum Rack.|  
|Wiederholen Sie diese Schritte für den nächsten Knoten oder Komponente|Wiederholen Sie die folgenden Schritte aus, um den nächsten Knoten oder eine andere Komponente der Anwendung in das Rechenzentrum verschieben.|  
  
## <a name="AfterMoving"></a>Zusätzliche Komponenten installieren  
Verwenden Sie die folgende Checkliste, um die zusätzlichen Komponenten zu installieren.  
  
|Aufgabe|Description||  
|--------|---------------|-|  
|Entpacken und rack-Netzwerkswitches und PDUs|Verwenden Sie die Rack-Diagramme, um die Netzwerkswitches und PDUs am richtigen Speicherort in das Gestell zu platzieren.||  
|Schließen Sie die Infiniband und Ethernet-Kabel gemäß den Bezeichnungen Kabel|Finden Sie unter Verkabelungsdiagramm. Jedes Kabel hat die Bezeichnung an beiden Enden, der angibt, in denen er verbunden sein muss.||  
|Schließen Sie alle Netzkabel|Finden Sie unter Verkabelungsdiagramm.||  
|Aktivieren Sie die Stromversorgung erneut mit den Racks und der PDUs|Verbinden Sie die Stromversorgung erneut mit den Racks und aus den Racks an die PDUs. **Schalten Sie nicht auf einem anderen Gerät Komponenten zu diesem Zeitpunkt.**||  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
