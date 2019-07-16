---
title: Lösungen für Remotedatenzugriff | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS [ADO]
ms.assetid: d311cc67-7db7-4c43-9590-d465564695e4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 40485562c8385e05ced033062563d5c5165218de
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67922175"
---
# <a name="solutions-for-remote-data-access"></a>Lösungen für den Remotedatenzugriff
## <a name="the-issue"></a>Das Problem  
 ADO kann es sich um die Anwendung direkt erhalten Zugriff auf und Ändern von Datenquellen (manchmal auch als ein System mit zwei Ebenen bezeichnet). Z. B. wenn die Verbindung mit der Datenquelle ist, die Ihre Daten enthält, ist, die eine direkte Verbindung in einem System mit zwei Ebenen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Möglicherweise möchten jedoch indirekt über eine Zwischenstufe wie z. B. Microsoft® Internet Information Services (IIS) den Zugriff auf Datenquellen. Diese Anordnung ist ein System mit drei Ebenen bezeichnet. IIS ist ein Client/Server-System, das eine effiziente Möglichkeit für eine lokale oder -Clients Anwendung zum Aufrufen einer Remote oder Server-Programms über das Internet oder Intranet bereitstellt. Die Server-Anwendung erhält Zugriff auf die Datenquelle und optional die erfassten Daten verarbeitet.  
  
 Ihre Intranet-Webseite enthält beispielsweise eine Anwendung, die in Microsoft® Visual Basic Scripting Edition (VBScript), das für die Verbindung zu IIS geschrieben wurde. IIS wiederum eine Verbindung mit der tatsächlichen Datenquelle her, die Daten abruft, verarbeitet diese in irgendeiner Form und klicken Sie dann die verarbeitete Informationen an die Anwendung zurückgegeben.  
  
 In diesem Beispiel verbunden die Anwendung nie direkt mit der Datenquelle; IIS wurde. Und IIS Zugriff auf die Daten mithilfe von ADO.  
  
> [!NOTE]
>  Die Client/Server-Anwendung muss nicht auf das Internet oder Intranet basieren (d. h. webbasierte)-Es könnte darin bestehen, ausschließlich der kompilierte Programme auf einem lokalen Netzwerk. Allerdings ist der Normalfall eine webbasierte Anwendung.  
  
 Da einige visual Kontrolle, z. B. ein Raster, Kontrollkästchen oder Liste, die zurückgegebene Informationen verwenden kann, muss die zurückgegebene Informationen einfach durch ein visuelles Steuerelement verwendet werden.  
  
 Sie möchten eine einfache und effiziente Anwendungsprogrammierschnittstelle, die Systemen mit drei Ebenen unterstützt und gibt Informationen zurück wie ganz einfach, als ob es abgerufen wurden auf einem System mit zwei Ebenen. Remote Data Service (RDS) ist diese Schnittstelle.  
  
## <a name="the-solution"></a>Die Lösung  
 RDS definiert ein Programmiermodell zur Verfügung: die Abfolge von Aktivitäten, die zum Zugriff auf und Aktualisieren einer Datenquelle – für den Zugriff auf Daten über einen Vermittler, z. B. Internet Information Services (IIS) erforderlich sind. Das Programmiermodell zusammengefasst, die gesamte Funktionalität von RDS.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes RDS-Programmiermodell](../../../ado/guide/remote-data-service/basic-rds-programming-model.md)   
 [RDS-Architektur](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [RDS-Tutorial](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Verwendung und Sicherheit von RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


