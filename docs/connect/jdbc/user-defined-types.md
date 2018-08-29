---
title: Benutzerdefinierte Typen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 19a71b27-b788-43a3-a76d-fe3001a6f016
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 55db7c7c903f4b22a85f9762f13f845ea7ea17ba
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785646"
---
# <a name="user-defined-types"></a>Benutzerdefinierte Typen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Benutzerdefinierte Typen (UDTs) wurden in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] vorgestellt. Mit ihnen können Entwickler das Skalartypsystem durch das Speichern von CLR-Objekten (Common Language Runtime) in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank erweitern. UDTs können mehrere Elemente enthalten und Verhalten aufweisen, die sich von den herkömmlichen Aliasdatentypen unterscheiden, die aus einem einzigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemdatentyp bestehen. Vorher waren UDTs auf eine Dateigröße von maximal 8 Kilobyte beschränkt. Ab [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] werden UDTs über 64 Kilobyte unterstützt. Ab Version 3.0 unterstützt JDBC Driver beim Festlegen des UserDefined-Formats auch UDTs, die größer als 64 KB sind.

UDTs mit genau oder weniger als 8.000 Byte verhalten sich also genau wie bisher. Größere UDTs werden aber unterstützt und zeigen ihre Größe als "unbegrenzt" an.

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Grundlegendes zu den Datentypen in JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)
