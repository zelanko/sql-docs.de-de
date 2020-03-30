---
title: Benutzerdefinierte Typen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 19a71b27-b788-43a3-a76d-fe3001a6f016
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3ed890ee562d3fcc2221877b23ee09bbf9a8ccf9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "69027137"
---
# <a name="user-defined-types"></a>Benutzerdefinierte Typen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Benutzerdefinierte Typen (UDTs) wurden in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] vorgestellt. Mit ihnen können Entwickler das Skalartypsystem durch das Speichern von CLR-Objekten (Common Language Runtime) in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank erweitern. UDTs können mehrere Elemente enthalten und Verhalten aufweisen, die sich von den herkömmlichen Aliasdatentypen unterscheiden, die aus einem einzigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemdatentyp bestehen. Vorher waren UDTs auf eine Dateigröße von maximal 8 Kilobyte beschränkt. Ab [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] werden UDTs über 64 Kilobyte unterstützt. Ab Version 3.0 unterstützt JDBC Driver beim Festlegen des UserDefined-Formats auch UDTs, die größer als 64 KB sind.

UDTs mit genau oder weniger als 8.000 Byte verhalten sich also genau wie bisher. Größere UDTs werden aber unterstützt und zeigen ihre Größe als "unbegrenzt" an.

## <a name="see-also"></a>Weitere Informationen

[Grundlegendes zu den Datentypen des JDBC-Treibers](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)
