---
title: Informationen zu Treibern und Datenquellen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7dffeea3bea7e3fbfa66e534ecaa758fbc2064d5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307221"
---
# <a name="about-drivers-and-data-sources"></a>Informationen zu Treibern und Datenquellen
*Treiber* sind die Komponenten, die ODBC-Anforderungen verarbeiten und Daten an die Anwendung zurückgeben. Bei Bedarf ändern Treiber die Anforderung einer Anwendung in ein Formular, das von der Datenquelle verstanden wird. Sie müssen das Setupprogramm des Treibers verwenden, um einen Treiber von Ihrem Computer hinzuzufügen oder zu löschen.  
  
 *Datenquellen* sind die Datenbanken oder Dateien, auf die ein Treiber zugreift und die durch einen Datenquellennamen (Data Source Name, DSN) identifiziert werden. Verwenden Sie den ODBC-Datenquellenadministrator, um Datenquellen aus Ihrem System hinzuzufügen, zu konfigurieren und zu löschen. Die Typen von Datenquellen, die verwendet werden können, werden in der folgenden Tabelle beschrieben.  
  
|Datenquelle|Beschreibung|  
|-----------------|-----------------|  
|Benutzer|Benutzer-DSNs sind auf einem Computer lokal und können nur vom aktuellen Benutzer verwendet werden. Sie sind in der HKEY_CURRENT_USER Registrierungsunterstruktur registriert.|  
|System|System-DSNs sind lokal auf einem Computer und nicht für einen Benutzer bestimmt. Das System oder jeder Benutzer mit Berechtigungen kann eine Datenquelle verwenden, die mit einem System-DSN eingerichtet wurde. System-DSNs sind in der HKEY_LOCAL_MACHINE Registrierungsunterstruktur registriert.|  
|Datei|Datei-DSNs sind dateibasierte Quellen, die von allen Benutzern gemeinsam genutzt werden können, die dieselben Treiber installiert haben und daher Zugriff auf die Datenbank haben. Diese Datenquellen müssen weder einem Benutzer als auch nicht lokal für einen Computer gewidmet sein. Dateidatenquellennamen werden nicht durch dedizierte Registrierungseinträge identifiziert. Stattdessen werden sie durch einen Dateinamen mit einer Dsn-Erweiterung identifiziert.|  
  
 Benutzer- und Systemdatenquellen werden zusammen als *Computerdatenquellen* bezeichnet, da sie lokal auf einem Computer sind.  
  
 Jede dieser Datenquellen verfügt über eine Registerkarte im Dialogfeld **ODBC-Datenquellenadministrator.** Weitere Informationen zu Datenquellen finden Sie unter [Datenquellen](../../odbc/reference/data-sources.md).
