---
title: Hardwareinstallation
description: In diesem Artikel wird beschrieben, wie Sie die Hardware für Ihre SQL Server PDW Appliance verschieben, entpacken und installieren. Dieser Artikel dient nur zu Informationszwecken und soll Ihnen helfen, den Prozess zu verstehen. Ihre Appliance sollte entpackt, installiert und überprüft werden, bevor Sie auf Sie über geschaltet wird. Kundenbeteiligung ist für Elemente wie den Zugriff auf Rechenzentren, Stromversorgung und Ethernet-Verbindungen erforderlich.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 60e27e2251cd2f613ca00266d76d4aaaf3b5c442
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401124"
---
# <a name="hardware-installation-for-analytics-platform-system-aps-appliance"></a>Hardware Installation für das Analytics Platform System (APS)-Gerät
In diesem Artikel wird beschrieben, wie Sie die Hardware für Ihre SQL Server PDW Appliance verschieben, entpacken und installieren. Dieser Artikel dient nur zu Informationszwecken und soll Ihnen helfen, den Prozess zu verstehen. Ihre Appliance sollte entpackt, installiert und überprüft werden, bevor Sie auf Sie über geschaltet wird. Kundenbeteiligung ist für Elemente wie den Zugriff auf Rechenzentren, Stromversorgung und Ethernet-Verbindungen erforderlich.  
  
## <a name="BeforeMoving"></a>Vor dem Verschieben von Komponenten aus dem Lade Dock  
Führen Sie die folgenden Aufgaben aus, bevor Sie die Gerätekomponenten verschieben, entpacken oder Rack ausführen.  
  
|Aufgabe|Beschreibung|  
|--------|---------------|  
|Überprüfen, ob alle Komponenten eingetroffen sind|Verwenden Sie die Bill of Materials (BOM), um zu überprüfen, ob alle Komponenten eingetroffen sind und sich auf Ihren Paletten am empfangenden Dock für Ihr Rechenzentrum befinden.|  
|Vergewissern Sie sich, dass das Rechenzentrum alle Anforderungen für das Gerät erfüllt.|Starten Sie diese Aufgabe durch Überprüfen der Hardware Spezifikationen und der Verkabelung, die von ihrer IHV bereitgestellt werden. In den nächsten Schritten finden Sie Einzelheiten zum Regal-und konnektivitätsbedarf.|  
|Stellen Sie sicher, dass das Rechenzentrum über den richtigen Regalbereich verfügt|Stellen Sie sicher, dass das Rechenzentrum über ausreichend Speicherplatz für alle Appliance-Racks verfügt.<br /><br />Vergewissern Sie sich, dass der Rack Leerraum leer ist und bereit ist, die Geräte Racks zu empfangen.|  
|Stellen Sie sicher, dass das Rechenzentrum Verbindungsanforderungen erfüllt.|Vergewissern Sie sich, dass das Rechenzentrum die Verkabelung-Anforderungen in den Verkabelung-Diagrammen erfüllt.<br /><br />Vergewissern Sie sich, dass Platz für alle Kabel und Netzkabel vorhanden ist, nachdem die Geräteknoten gecluckt wurden.|  
|Überprüfen Sie, ob die Fußböden zwischen dem Dock und den Racks den Gewichtungs Anforderungen entsprechen.|Stellen Sie sicher, dass der gesamte Fußboden zwischen den Paletten und den Racks die Gewichtung der Geräteknoten unterstützen kann, insbesondere in Rechenzentren mit erhöhten Ebenen.<br /><br />Wenden Sie sich an Ihren IHV, um Informationen zur Gewichtung der einzelnen Komponenten zu erhalten.|  
|Sichern des Daten Center Racks|Sichern Sie das Gestell des Rechenzentrums mit zusätzlichen Geräten, die für den Standort Ihres Rechenzentrums erforderlich sind, z. b. Erdbeben Bänder in geografischen Bereichen, die für Erdbeben anfällig sind.|  
|Vorbereiten der Unterstützung beim Transportieren der Komponenten|Legen Sie im Voraus fest, welche Unterstützung, Ausrüstung und Tools Sie benötigen, um die einzelnen Komponenten sicher und ohne Beschädigung zu verarbeiten.|  
  
## <a name="Moving"></a>Verschieben der Racks aus dem Lade Dock in das Rechenzentrum  
Jede Palette enthält alle Komponenten für ein Geräte Gestell, einschließlich Knoten, Kabel, Kabel usw.  
  
Verwenden Sie die folgende Prüfliste, um jedes Appliance Gestell von der Palette an das Lade Dock an seine Regal Position im Rechenzentrum zu verschieben. Verschieben Sie zuerst das Steuerelement Gestell, und verschieben Sie dann die anderen Gerätedaten Racks.  
  
> [!WARNING]  
> Wenn Sie diese Schritte nicht genau wie beschrieben ausführen, kann dies zu einer negativen Beschädigung, Beschädigung Ihrer SQL Server PDW Appliance oder zu anderen Problemen führen.  
>   
> Versuchen Sie niemals, einen Geräteknoten oder eine andere große Komponente ohne Unterstützung oder angemessene Ausrüstung zu entfernen oder zu verschieben. Wenden Sie sich an Ihren IHV, um Informationen zur Gewichtung der einzelnen Komponenten zu erhalten, damit Sie im voraus ermitteln können, welche Unterstützung, Ausrüstung und welche Tools Sie benötigen, um die einzelnen Komponenten sicher und ohne Beschädigung zu verarbeiten.  
  
|Aufgabe|Beschreibung|  
|--------|---------------|  
|Überprüfen Sie, ob die Palette die Ebene hat|Bevor Sie beginnen, die Palette zu verschieben oder zu entpacken, stellen Sie sicher, dass Sie sich auf der Ebene befindet.|  
|Entbolt eines Knotens aus der Palette|Wenn Sie am oberen Rand der Palette beginnen, Entschrauben Sie den obersten Knoten aus der Palette.|  
|Verschieben Sie den Knoten in einen Dolly oder Warenkorb, der das Gewicht unterstützen kann.|Verwenden Sie Rampen und geeignete Verfahren zum Verschieben und verschieben, um den Knoten in einen Dolly oder Warenkorb zu verschieben, der das Gewicht unterstützen kann.|  
|Transportieren Sie den Knoten in das Rechenzentrum.|Verwenden Sie geeignete Verfahren zum Verschieben und verschieben, um den Knoten im Rechenzentrum in die Position zu verschieben.|  
|Sichern Sie den Knoten im Rechenzentrums Rack|Sichern Sie den Knoten im Rechenzentrums Rack.|  
|Wiederholen Sie diese Schritte für den nächsten Knoten oder die nächste Komponente.|Wiederholen Sie diese Schritte, um den nächsten Knoten oder eine andere Geräte Komponente in das Rechenzentrum zu verschieben.|  
  
## <a name="AfterMoving"></a>Installieren zusätzlicher Komponenten  
Verwenden Sie die folgende Checkliste, um die zusätzlichen Komponenten zu installieren.  
  
|Aufgabe|Beschreibung||  
|--------|---------------|-|  
|Entpacken und Gestell von Netzwerk Switches und PDUs|Verwenden Sie die Regal Diagramme, um die Netzwerk Switches und PDUs an der richtigen Stelle im Gestell zu platzieren.||  
|Verbinden der InfiniBand-und Ethernet-Kabel gemäß den Kabel Bezeichnungen|Siehe das Verkabelung-Diagramm. Jedes Kabel hat eine Bezeichnung an jedem Ende, das angibt, an welcher Stelle eine Verbindung hergestellt werden muss.||  
|Verbinden aller Netzkabel|Siehe das Verkabelung-Diagramm.||  
|Schalten Sie die Stromversorgung für die Racks und die PDUs ein.|Verbinden Sie die Stromversorgung mit den Racks und aus den Racks mit dem PDUs. **Schalten Sie zurzeit keine der anderen Appliance-Komponenten ein.**||  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
