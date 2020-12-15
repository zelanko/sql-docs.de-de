---
title: Richtlinien und Einschränkungen von SQLXML 4.0
description: Erfahren Sie mehr über die Richtlinien und Einschränkungen bei der Arbeit mit SQLXML 4,0.
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, about SQLXML
ms.assetid: fe433d30-90a1-421e-85c6-af13294dc18d
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 305565d542144a7e6e24663aadba1fb56a67eddb
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97431296"
---
# <a name="guidelines-and-limitations-of-sqlxml-40"></a>Richtlinien und Einschränkungen von SQLXML 4.0
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Bei der Arbeit mit SQLXML 4.0 gilt Folgendes:  
  
-   Das als Abfrageergebnis zurückgegebene XML wird nicht anhand des Zuordnungsschemas, das das XML erstellt hat, überprüft.  
  
-   SQLXML 4.0 umfasst versionsunabhängige und versionsabhängige Programm-IDs. Es wird empfohlen, dass alle Produktionsanwendungen versionsabhängige Programm-IDs verwenden. Dies ist besonders wichtig, da SQLXML 4.0 nicht vollständig abwärtskompatibel ist. Die Verwendung von versionsabhängige Programm-IDs schützt vor möglichen Produktionsfehlern beim Installieren neuerer Versionen. Mit jeder neuen Version kann sich das Programmverhalten aus verschiedenen Gründen, z. B. aufgrund von Fehlerbehebungen, möglichen Designänderungen usw. ändern. Die Verwendung von versionsabhängigen Programm-IDs schützt vor unerwarteten Fehlern beim Installieren neuerer Versionen. Wenn Sie eine neuere Version installieren, arbeitet die Anwendung bei versionsabhängigen Programm-IDs weiterhin fehlerfrei. Wenn Sie die vorherigen versionsabhängigen Programm-IDs ändern und die aktuelle versionsabhängigen Programm-IDs in einer neueren Version verwenden, müssen Sie die Anwendung erst testen, bevor Sie die Arbeit damit aufnehmen. Anwendungen mit versionsunabhängigen Programm-IDs schlagen beispielsweise möglicherweise im folgenden Szenario fehl:  
  
     Sie führen eine Anwendung aus, die SQLXML 4.0 und versionsunabhängige Programm-IDs verwendet, und Sie installieren einige andere Softwareprogramme. Dabei könnte mit diesem Programm eine frühere Version von SQLXML installiert werden. Ihre Anwendung schlägt fehl, da die versionsunabhängigen Programm-IDs in der Anwendung nun auf die frühere Version von SQLXML verweisen, die nur bedingt über das SQLXML-Funktion verfügen, das Ihre Anwendung verwendet.  
  
-   Wenn Sie aus irgendeinem Grund den SQLXMLOLEDB-Anbieter nicht verwenden möchten und stattdessen den SQLOLEDB-Anbieter für SQLXML-Funktionen verwenden möchten, legen Sie die **SQLXML-Version** -Eigenschaft auf "SQLXML. 4.0" fest.  
  
  
