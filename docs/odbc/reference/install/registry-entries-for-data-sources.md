---
title: Registrierungseinträge für Datenquellen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC]
- data sources [ODBC], registry entries
- registry entries for data sources [ODBC], about registry entries
- data sources [ODBC], configuring
- registry entries for data sources [ODBC]
ms.assetid: 78aaa3d3-d081-4550-80e3-720c910d5996
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c73ea704b091bc37afb1ac42b520304022d929c3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296270"
---
# <a name="registry-entries-for-data-sources"></a>Registrierungseinträge für Datenquellen
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur explizit auf früheren Windows-Versionen installieren.  
  
 Die Installations-DLL verwaltet Informationen in der Registrierung zu jeder Datenquelle. In Microsoft Windows NT/Windows 2000 und Microsoft Windows 95/98 werden diese Informationen in Unterschlüsseln unter einem der beiden folgenden Schlüssel in der Registrierung gespeichert:  

 ```console
 HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\Odbc.ini  
 ```

 ```console
 HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini
 ```

 Welcher Schlüssel verwendet wird, hängt davon ab, ob es sich bei der Datenquelle um eine *Systemdatenquelle handelt,* die allen Benutzern zur Verfügung steht, oder um eine *Benutzerdatenquelle,* die nur für den aktuellen Benutzer verfügbar ist. Systemdatenquellen werden in der HKEY_LOCAL_MACHINE-Struktur gespeichert, und Benutzerdatenquellen werden in der HKEY_CURRENT_USER-Struktur gespeichert. Ansonsten sind Systemdatenquellen und Benutzerdatenquellen identisch.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Unterschlüssel für ODBC-Datenquellen](../../../odbc/reference/install/odbc-data-sources-subkey.md)  
  
-   [Unterschlüssel für Datenquellenspezifikationen](../../../odbc/reference/install/data-source-specification-subkeys.md)  
  
-   [Standardunterschlüssel](../../../odbc/reference/install/default-subkey.md)  
  
-   [ODBC-Unterschlüssel](../../../odbc/reference/install/odbc-subkey.md)
