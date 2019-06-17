---
title: Informationen zu Treibern und Datenquellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC data source administrator [ODBC], concepts
ms.assetid: 2bb83ef1-4bbe-4be3-8c32-c4d1140aae1d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 69516a613cbd9071686067350ced2ce5ca166a27
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63294450"
---
# <a name="about-drivers-and-data-sources"></a>Informationen zu Treibern und Datenquellen
*Treiber* sind die Komponenten, die ODBC-Anforderungen verarbeitet und Daten an die Anwendung zurück. Ggf. Ändern der Treiber die Anforderung einer Anwendung in ein Format, das von der Datenquelle erkannt wird. Sie müssen den Treiber des Setup-Programm verwenden, zum Hinzufügen oder Löschen einen Treiber auf Ihrem Computer.  
  
 *Datenquellen* sind die Datenbanken oder Dateien, die von einem Treiber zugegriffen und durch einen Datenquellennamen (DSN) identifiziert. Verwenden Sie den ODBC-Datenquellen-Administrator hinzufügen, konfigurieren und Löschen von Datenquellen aus dem System. Die Typen von Datenquellen, die verwendet werden können, werden in der folgenden Tabelle beschrieben.  
  
|Datenquelle|Beschreibung|  
|-----------------|-----------------|  
|Benutzer|Benutzer-DSNs werden lokal auf einem Computer und können nur durch den aktuellen Benutzer verwendet werden. Sie werden in der Teilstruktur der HKEY_CURRENT_USER-Registrierung registriert.|  
|System|System-DSNs werden lokal auf einem Computer statt für einen Benutzer bestimmt. Das System oder alle Benutzer mit Berechtigungen können eine Datenquelle mit einer System-DSN einrichten. System-DSNs werden in der HKEY_LOCAL_MACHINE-Registrierungsunterstruktur registriert.|  
|Datei|Datei-DSNs werden dateibasierte Datenquellen, die freigegeben werden können, von allen Benutzern, die die gleichen Treiber installiert haben und daher Zugriff auf die Datenbank. Diese Datenquellen müssen nicht ausschließlich für einen Benutzer noch lokal auf einem Computer sein. Datei-Datenquellennamen werden nicht durch dedizierte Registrierungseinträge bezeichnet. Stattdessen werden sie durch einen Dateinamen mit der Erweiterung ".DSN" identifiziert.|  
  
 Benutzer und System-Datenquellen werden zusammen als bezeichnet *Computer* -Datenquellen, da sie sich lokal auf einem Computer befinden.  
  
 Jede dieser Datenquellen verfügt über eine Registerkarte der **ODBC-Datenquellenadministrator** Dialogfeld. Weitere Informationen zu Datenquellen finden Sie unter [Datenquellen](../../odbc/reference/data-sources.md).
