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
ms.openlocfilehash: 4e9b7229882b3b7f94e6b059e04c6496bde09641
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938044"
---
# <a name="about-drivers-and-data-sources"></a>Informationen zu Treibern und Datenquellen
*Treiber* sind die Komponenten, die ODBC-Anforderungen verarbeiten und Daten an die Anwendung zurückgeben. Bei Bedarf ändern Treiber die Anforderung einer Anwendung in ein Formular, das von der Datenquelle verstanden wird. Sie müssen das Setup Programm des Treibers verwenden, um einen Treiber von Ihrem Computer hinzuzufügen oder zu löschen.  
  
 *Datenquellen* sind die Datenbanken oder Dateien, auf die ein Treiber zugreift und die durch einen Datenquellen Namen (DSN) identifiziert werden. Verwenden Sie den ODBC-Datenquellen-Administrator zum Hinzufügen, konfigurieren und Löschen von Datenquellen in Ihrem System. In der folgenden Tabelle werden die Typen von Datenquellen beschrieben, die verwendet werden können.  
  
|Datenquelle|BESCHREIBUNG|  
|-----------------|-----------------|  
|Benutzer|Benutzer-DSNs sind auf einem Computer lokal und können nur vom aktuellen Benutzer verwendet werden. Sie werden in der Unterstruktur der HKEY_CURRENT_USER Registrierung registriert.|  
|System|System-DSNs sind auf einem Computer lokal, anstatt für einen Benutzer dediziert zu werden. Das System oder ein beliebiger Benutzer mit Berechtigungen kann eine Datenquelle verwenden, die mit einem System-DSN eingerichtet ist. System-DSNs werden in der HKEY_LOCAL_MACHINE Registrierungs Unterstruktur registriert.|  
|Datei|Datei-DSNs sind dateibasierte Quellen, die von allen Benutzern gemeinsam genutzt werden können, die die gleichen Treiber installiert haben und daher Zugriff auf die Datenbank haben. Diese Datenquellen müssen keinem Benutzer zugewiesen werden, und Sie müssen nicht auf einem Computer lokal sein. Datei Datenquellen Namen werden nicht durch dedizierte Registrierungseinträge identifiziert. Stattdessen werden Sie durch einen Dateinamen mit der Erweiterung. DSN identifiziert.|  
  
 Benutzer-und Systemdaten Quellen werden zusammen als Computer Datenquellen bezeichnet *, da Sie* auf einem Computer lokal sind.  
  
 Jede dieser Datenquellen verfügt über eine Registerkarte im Dialogfeld **ODBC-Datenquellen-Administrator** . Weitere Informationen zu Datenquellen finden Sie unter [Datenquellen](../../odbc/reference/data-sources.md).
