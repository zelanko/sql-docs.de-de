---
title: Richtlinien und Einschränkungen von SQLXML 4.0 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLXML, about SQLXML
ms.assetid: fe433d30-90a1-421e-85c6-af13294dc18d
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 10aa9e6c97afbd62e9608f394b38717a677edf0d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058463"
---
# <a name="guidelines-and-limitations-of-sqlxml-40"></a>Richtlinien und Einschränkungen von SQLXML 4.0
  Bei der Arbeit mit SQLXML 4.0 gilt Folgendes:  
  
-   Das als Abfrageergebnis zurückgegebene XML wird nicht anhand des Zuordnungsschemas, das das XML erstellt hat, überprüft.  
  
-   SQLXML 4.0 umfasst versionsunabhängige und versionsabhängige Programm-IDs. Es wird empfohlen, dass alle Produktionsanwendungen versionsabhängige Programm-IDs verwenden. Dies ist besonders wichtig, da SQLXML 4.0 nicht vollständig abwärtskompatibel ist. Die Verwendung von versionsabhängige Programm-IDs schützt vor möglichen Produktionsfehlern beim Installieren neuerer Versionen. Mit jeder neuen Version kann sich das Programmverhalten aus verschiedenen Gründen, z. B. aufgrund von Fehlerbehebungen, möglichen Designänderungen usw. ändern. Die Verwendung von versionsabhängigen Programm-IDs schützt vor unerwarteten Fehlern beim Installieren neuerer Versionen. Wenn Sie eine neuere Version installieren, arbeitet die Anwendung bei versionsabhängigen Programm-IDs weiterhin fehlerfrei. Wenn Sie die vorherigen versionsabhängigen Programm-IDs ändern und die aktuelle versionsabhängigen Programm-IDs in einer neueren Version verwenden, müssen Sie die Anwendung erst testen, bevor Sie die Arbeit damit aufnehmen. Anwendungen mit versionsunabhängigen Programm-IDs schlagen beispielsweise möglicherweise im folgenden Szenario fehl:  
  
     Sie führen eine Anwendung aus, die SQLXML 4.0 und versionsunabhängige Programm-IDs verwendet, und Sie installieren einige andere Softwareprogramme. Dabei könnte mit diesem Programm eine frühere Version von SQLXML installiert werden. Ihre Anwendung schlägt fehl, da die versionsunabhängigen Programm-IDs in der Anwendung nun auf die frühere Version von SQLXML verweisen, die nur bedingt über das SQLXML-Funktion verfügen, das Ihre Anwendung verwendet.  
  
-   Wenn aus irgendeinem Grund Sie nicht den SQLXMLOLEDB-Anbieter verwendet werden soll, und möchten stattdessen den SQLOLEDB-Anbieter für SQLXML-Funktionen, legen Sie die **SQLXML Version** -Eigenschaft auf "SQLXML.4.0".  
  
  